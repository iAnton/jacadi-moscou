<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app clipped floating>
      <v-row>
        <v-col cols="12">
          <v-img
            src="https://www.jacadi.co.uk/_ui/desktop/assets/img/jacadi-logo-without-crown.svg"
            width="139"
            class="mx-auto"
          ></v-img>
        </v-col>
      </v-row>
      <v-list dense>
        <!-- <v-list-item @click="!drawer">
          <v-list-item-content>
            <v-list-item-title>FAQ Covid-19</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item @click="!drawer">
          <v-list-item-content>
            <v-list-item-title>#stayathome</v-list-item-title>
          </v-list-item-content>
        </v-list-item> -->
        <v-list-group
          v-for="item in firstItems"
          :key="item.title"
          v-model="item.active"
        >
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title
                :class="{
                  'font-weight-bold': item.title === 'New Arrivals'
                }"
                v-text="item.title"
              ></v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item
            v-for="subItem in item.items"
            :key="subItem.title"
            nuxt
            :to="`/${subItem.title}`"
          >
            <v-list-item-content>
              <v-list-item-title v-text="subItem.title"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
        <v-list-item @click="!drawer">
          <v-list-item-content>
            <v-list-item-title class="red--text font-weight-bold"
              >Распродажа</v-list-item-title
            >
          </v-list-item-content>
        </v-list-item>
        <v-list-item @click="!drawer">
          <v-list-item-content>
            <v-list-item-title>Особый случай</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-group
          v-for="item in secondItems"
          :key="item.title"
          v-model="item.active"
        >
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title v-text="item.title"></v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item
            v-for="subItem in item.items"
            :key="subItem.title"
            nuxt
            :to="`/${subItem.title}`"
          >
            <v-list-item-content>
              <v-list-item-title v-text="subItem.title"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
        <v-list-item
          v-for="item in itemsNotGroup"
          :key="item.title"
          @click="$router.push('/')"
        >
          <v-list-item-content>
            <v-list-item-title v-text="item.title"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      app
      clipped-left
      color="#8798bf"
      class="white--text"
      elevation="0"
    >
      <v-app-bar-nav-icon
        class="white--text"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-toolbar-title>
        <nuxt-link class="white--text mr-4" to="/">Jacadi Москва</nuxt-link>
      </v-toolbar-title>
      <!-- <nuxt-link class="white--text" to="/">The e-gift card</nuxt-link> -->
      <v-spacer></v-spacer>
      <!-- <v-col>
            <nuxt-link class="white--text" to="/"
              >The eshop is open, check our FAQ ></nuxt-link
            >
          </v-col> -->
      <!-- </v-col
        > -->
      <!-- <v-text-field
        class="mx-4"
        flat
        hide-details
        prepend-inner-icon="search"
        solo
      ></v-text-field> -->
      <!-- <nuxt-link class="d-flex flex-column mx-2" to="/">
        <v-icon>mdi-map-marker</v-icon>
        <span>Магазины</span>
      </nuxt-link>
      <nuxt-link class="d-flex flex-column mx-2" to="/">
        <v-icon>mdi-account</v-icon>
        <span>Аккаунт</span>
      </nuxt-link>
      <nuxt-link class="d-flex flex-column mx-2" to="/">
        <v-icon>mdi-heart</v-icon>
        <span>Избранное</span>
      </nuxt-link>
      <nuxt-link class="d-flex flex-column mx-2" to="/">
        <v-icon>mdi-cart</v-icon>
        <span>Корзина</span>
      </nuxt-link> -->
      <!-- </v-row> -->
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <v-row class="mb-6" no-gutters>
          <v-col cols="12">
            <v-row no-gutters>
              <v-col cols="6">
                <v-text-field
                  v-model="search"
                  label="Search"
                  append-icon="mdi-magnify"
                  single-line
                  outlined
                  dense
                ></v-text-field>
              </v-col>
              <v-spacer></v-spacer>
              <v-col cols="6" sm="auto">
                <nav class="d-none d-lg-block">
                  <ul class="d-flex text-caption text-no-wrap">
                    <nuxt-link to="/locations" class="d-flex flex-column mr-6">
                      <v-icon>mdi-map-marker</v-icon>
                      <span>Boutique Locations</span>
                    </nuxt-link>
                    <nuxt-link to="/account" class="d-flex flex-column mr-6">
                      <v-icon>mdi-account</v-icon>
                      <span>My Account</span>
                    </nuxt-link>
                    <nuxt-link to="/wishlist" class="d-flex flex-column mr-6">
                      <v-icon>mdi-heart</v-icon>
                      <span>Wishlist</span>
                    </nuxt-link>
                    <nuxt-link to="/cart" class="d-flex flex-column">
                      <v-icon>mdi-cart</v-icon>
                      <span>Shopping Bag</span>
                    </nuxt-link>
                  </ul>
                </nav>
                <nav class="d-lg-none">
                  <ul class="d-flex text-caption text-no-wrap">
                    <nuxt-link
                      to="/locations"
                      class="d-flex flex-column mr-2 mr-lg-6"
                    >
                      <v-icon>mdi-map-marker</v-icon>
                    </nuxt-link>
                    <nuxt-link
                      to="/account"
                      class="d-flex flex-column mr-2 mr-lg-6"
                    >
                      <v-icon>mdi-account</v-icon>
                    </nuxt-link>
                    <nuxt-link
                      to="/wishlist"
                      class="d-flex flex-column mr-2 mr-lg-6"
                    >
                      <v-icon>mdi-heart</v-icon>
                    </nuxt-link>
                    <nuxt-link to="/cart" class="d-flex flex-column">
                      <v-icon>mdi-cart</v-icon>
                    </nuxt-link>
                  </ul>
                </nav>
              </v-col>
            </v-row>
            <v-col cols="12">
              <v-breadcrumbs :items="breadcrumbs" class="hidden-sm-and-down">
                <template v-slot:divider>
                  <v-icon>mdi-chevron-right</v-icon>
                </template>
              </v-breadcrumbs>
              <nuxt />
            </v-col>
          </v-col>
        </v-row>
        <v-divider></v-divider>
        <v-row>
          <v-col class="d-flex justify-space-around">
            <div class="d-flex flex-column flex-lg-row align-center mx-4">
              <v-icon class="pa-4">mdi-phone</v-icon>
              <div class="d-flex flex-column text-center align-center mx-4">
                <span>Customer service</span>
                <nuxt-link to="/" class="d-none d-lg-block"
                  >Подробнее</nuxt-link
                >
              </div>
            </div>
            <div class="d-flex flex-column flex-lg-row align-center mx-4">
              <v-icon class="pa-4">mdi-sync</v-icon>
              <div class="d-flex flex-column text-center align-center mx-4">
                <span>Free returns</span>
                <nuxt-link to="/" class="d-none d-lg-block"
                  >Подробнее</nuxt-link
                >
              </div>
            </div>
          </v-col>
          <v-col class="d-flex justify-space-around">
            <div class="d-flex flex-column flex-lg-row align-center mx-4">
              <v-icon class="pa-4">mdi-train-car</v-icon>
              <div class="d-flex flex-column text-center align-center mx-4">
                <span>Free delivery over £50</span>
                <nuxt-link to="/" class="d-none d-lg-block"
                  >Подробнее</nuxt-link
                >
              </div>
            </div>
            <div class="d-flex flex-column flex-lg-row align-center mx-4">
              <v-icon class="pa-4">mdi-lock</v-icon>
              <div class="d-flex flex-column text-center align-center mx-4">
                <span>Secure payment</span>
                <nuxt-link to="/" class="d-none d-lg-block"
                  >Подробнее</nuxt-link
                >
              </div>
            </div>
          </v-col>
          <!-- <v-col
            class="d-flex flex-no-wrap justify-space-between align-content-center"
          >
            <div class="d-flex flex-column flex-lg-row">
              <v-icon class="pa-4">mdi-phone</v-icon>
              <div class="d-flex flex-column">
                <span>Поддержка</span>
                <nuxt-link to="/" class="d-none d-lg-block"
                  >Подробнее</nuxt-link
                >
              </div>
            </div>
            <div class="d-flex flex-column flex-lg-row">
              <v-icon class="pa-4">mdi-sync</v-icon>
              <div class="d-flex flex-column">
                <span>Бесплатный возврат товара</span>
                <nuxt-link to="/" class="d-none d-lg-block"
                  >Подробнее</nuxt-link
                >
              </div>
            </div>
            <div class="d-flex flex-column flex-lg-row">
              <v-icon class="pa-4">mdi-train-car</v-icon>
              <div class="d-flex flex-column">
                <span>Бесплатная доставка</span>
                <nuxt-link to="/" class="d-none d-lg-block"
                  >Подробнее</nuxt-link
                >
              </div>
            </div>
            <div class="d-flex flex-column flex-lg-row">
              <v-icon class="pa-4">mdi-lock</v-icon>
              <div class="d-flex flex-column">
                <span>Защищенные платежи</span>
                <nuxt-link to="/" class="d-none d-lg-block"
                  >Подробнее</nuxt-link
                >
              </div>
            </div>
          </v-col> -->
        </v-row>
        <v-divider></v-divider>
        <v-row class="d-flex flex-column flex-lg-row">
          <v-col>
            <div class="d-flex flex-column align-center">
              <h3 class="mb-2">Подписаться на рассылку</h3>
              <span class="caption mb-2"
                >Email sign up For further information about your personal data,
                <nuxt-link to="/">click here</nuxt-link></span
              >
              <div class="d-flex">
                <v-text-field label="E-mail" outlined dense></v-text-field>
                <v-btn
                  tile
                  color="#8798bf"
                  class="ml-1 white--text"
                  elevation="0"
                  >Ок</v-btn
                >
              </div>
            </div>
          </v-col>
          <v-col>
            <div class="d-flex flex-column align-center bordered">
              <h3 class="mb-2">Оставайтесь на связи</h3>
              <v-card width="100%" flat tile class="text-center">
                <v-card-text>
                  <v-btn tile class="mx-2" icon>
                    <svg class="j-icon">
                      <use
                        xmlns:xlink="http://www.w3.org/1999/xlink"
                        xlink:href="#icon-facebook-grey"
                      >
                        <svg
                          id="icon-facebook-grey"
                          viewBox="0 0 17.8 17.8"
                          fill="#3B5998"
                        >
                          <title>facebook-grey</title>
                          <g class="st1">
                            <path
                              class="st2"
                              d="M-407.9 589.2h1v12.7c0 1.3 1.1 2.4 2.4 2.4h7.5c1.3 0 2.4-1.1 2.4-2.4v-12.7h1c.2 0 .4-.2.4-.4s-.2-.4-.4-.4h-4c0-1.2-.9-2-2.1-2h-2c-1.2 0-2.2.9-2.2 2h-4c-.2 0-.4.2-.4.4s.3.4.4.4zm12.5 12.7c0 .9-.7 1.6-1.6 1.6h-7.5c-.9 0-1.6-.7-1.6-1.6v-12.7h10.7v12.7zm-7.5-13.5c0-.7.6-1.2 1.3-1.2h2.2c.7 0 1.3.5 1.3 1.2h-4.8z"
                            ></path>
                            <path
                              class="st2"
                              d="M-407.9 589.2c1.2 0 .9.1.9 1.3v4.7c0 2.2-.3 4.5 0 6.6.4 3.1 3.7 2.5 6 2.5 2 0 5.6.8 6.4-1.8.6-2 .1-4.7.1-6.8v-4.5c0-.4-.1-1.1 0-1.5.3-.8-.1-.1.4-.5.3-.2 1 .2 1-.5s-1.3-.4-1.7-.4c-.6 0-2 .3-2.5 0 .1 0-.3-1-.4-1.2-.5-.6-1.1-.7-1.8-.8-.9-.2-2.7-.2-3.5.4-.6.3-.6 1.4-.9 1.6-.2.1-1.3 0-1.7 0-.5 0-2.3-.3-2.6.1-.2.4 0 .7.3.8.1 0 .1-.1 0 0-1-.5 1.2-.8 1.2-.8h2.8s.1 0 .1-.1c0-2.6 6.3-2.7 6.3 0 0 0 0 .1.1.1h2.4c.3 0 .7-.1.9 0 .9.4.1.7-.5.7 0 0-.1 0-.1.1v9c0 1.1.2 2.6 0 3.7-.3 1.4-1.9 2.2-3.3 2.4-.9.1-1.9 0-2.8 0-2.1 0-5.7.6-6.1-2.4-.1-1.1 0-2.4 0-3.5v-9.2s0-.1-.1-.1h-1c.1 0 .1.1.1.1z"
                            ></path>
                            <path
                              class="st2"
                              d="M-395.4 601.9c-.1.5-1.4 1.4-1.9 1.6-.3.1-.6 0-.9 0h-3.2c-1.8 0-3.9.5-4.6-1.8-.3-1.2 0-3.1 0-4.4v-6c0-.4-.2-1.3 0-1.7.2-.6-.2-.1.3-.4 1.1-.5 3.8 0 5 0 1.3 0 3.7-.5 4.9 0 .6.2.4 1 .4 2v10.7c0 .1.1.1.1 0v-12.7s0-.1-.1-.1h-10.7s-.1 0-.1.1v6.6c0 2-.5 4.5.1 6.5.6 2.1 3.8 1.4 5.4 1.4 1.9 0 4.9.7 5.3-1.8.2-.1 0-.1 0 0zm-7.5-13.5c.2-1.5 2.1-1.1 3.1-1.1h.4c.2 0 .5.1.7.2.1.8.3 1.1.6.8h-4.3c-.2 0-.5-.1-.5.1 0-.1-.1-.1-.1 0h.1c1.5.1 3.2.1 4.8.1 0 0 .1 0 .1-.1 0-1.3-1.4-1.3-2.4-1.3-1.1 0-2.5-.1-2.6 1.3 0 .1.1.1.1 0z"
                            ></path>
                          </g>
                          <g class="st1">
                            <path
                              class="st2"
                              d="M-403.4 591.4c-.2 0-.4.2-.4.4v9.1c0 .2.2.4.4.4s.4-.2.4-.4v-9.1c.1-.2-.1-.4-.4-.4z"
                            ></path>
                            <path
                              class="st2"
                              d="M-403.4 591.3c-.5.3-.4.7-.4 1.2-.1 1.3 0 2.7 0 4 0 .6-.5 4.8.5 4.8s.5-4.3.5-4.8c0-1.3.1-2.7 0-4-.1-.5 0-.9-.6-1.2 0 0-.1.1 0 0 .9.5.3 4 .3 4.8v3.1c0 .5.2 1.6-.3 1.6-.6 0-.3-1-.3-1.5v-3.1c-.1-.7-.5-4.5.3-4.9.2.1 0 0 0 0z"
                            ></path>
                          </g>
                          <g class="st1">
                            <path
                              class="st2"
                              d="M-400.5 591.4c-.2 0-.4.2-.4.4v9.1c0 .2.2.4.4.4s.4-.2.4-.4v-9.1c0-.2-.3-.4-.4-.4z"
                            ></path>
                            <path
                              class="st2"
                              d="M-400.5 591.3c-.6.2-.4.6-.5 1.2-.1 1.3 0 2.7 0 4 0 .6-.5 4.8.5 4.8s.5-4.3.5-4.8c0-1.3.1-2.7 0-4-.1-.5.1-.9-.5-1.2 0 0-.1.1 0 0 .9.5.3 4 .3 4.8v3.1c0 .5.2 1.6-.3 1.6-.6 0-.3-1-.3-1.5v-3.1c-.1-.7-.6-4.5.3-4.9.1.1.1 0 0 0z"
                            ></path>
                          </g>
                          <g class="st1">
                            <path
                              class="st2"
                              d="M-398.1 591.8v9.1c0 .2.2.4.4.4s.4-.2.4-.4v-9.1c0-.2-.2-.4-.4-.4s-.4.2-.4.4z"
                            ></path>
                            <path
                              class="st2"
                              d="M-398.2 591.8v7.3c0 .4-.3 1.8.1 2.1.4.4.7 0 .8-.3.3-.6 0-1.9 0-2.5v-4.7c0-.4.3-1.9-.1-2.3-.4-.3-.6 0-.8.4 0 .1.1.1.1 0s.7.1.7.1c.1.1 0 .3 0 .3.1.2 0 .7 0 .9v6.1c0 .5.2 1.6-.3 1.6-.6 0-.3-1-.3-1.5v-7.6s-.2 0-.2.1z"
                            ></path>
                          </g>
                          <path
                            class="st1 st2"
                            d="M-397.4 603.8v-3.4c0-.2-.2-.2-.2 0v3.4c.1.2.2.2.2 0zm-.7 0v-3.4c0-.2-.2-.2-.2 0v3.4c-.1.2.2.2.2 0zm1.7-.2v-3.4c0-.2-.2-.2-.2 0v3.4c-.2.1.2.1.2 0zm.8-.1v-3.4c0-.2-.2-.2-.2 0v3.4c-.1.2.2.2.2 0zm-3.4.3v-3.4c0-.2-.2-.2-.2 0v3.4c-.2.2.2.2.2 0zm-.9-.1v-3.4c0-.2-.2-.2-.2 0v3.4c-.1.2.2.2.2 0zm-1-.1v-3.4c0-.2-.2-.2-.2 0v3.4c.1.2.2.2.2 0zm-.7.1v-3.4c0-.2-.2-.2-.2 0v3.4c-.1.1.2.1.2 0zm-.9-.1v-3.4c0-.2-.2-.2-.2 0v3.4c-.1.1.2.1.2 0zm-.9 0v-3.4c0-.2-.2-.2-.2 0v3.4c0 .1.2.1.2 0zm-1-.2V600c0-.2-.2-.2-.2 0v3.4c.1.2.2.2.2 0zm-.7 0V600c0-.2-.2-.2-.2 0v3.4c-.1.2.2.2.2 0z"
                          ></path>
                          <path
                            class="st3"
                            d="M16.8 0H1C.5 0 0 .4 0 1v15.8c0 .5.4 1 1 1h8.5V11H7.2V8.3h2.3v-2c0-2.3 1.4-3.5 3.4-3.5 1 0 1.9.1 2.1.1v2.4h-1.4c-1.1 0-1.3.5-1.3 1.3v1.7H15l-.4 2.6h-2.3v6.9h4.5c.5 0 1-.4 1-1V1c0-.5-.4-1-1-1z"
                          ></path>
                        </svg>
                      </use>
                    </svg>
                  </v-btn>
                  <v-btn tile class="mx-2" icon>
                    <svg class="j-icon">
                      <use
                        xmlns:xlink="http://www.w3.org/1999/xlink"
                        xlink:href="#icon-instagram-bleu"
                      >
                        <svg
                          id="icon-instagram-bleu"
                          viewBox="0 0 20.1 20.1"
                          fill="black"
                        >
                          <title>instagram-bleu</title>
                          <path
                            d="M1.2 17.1v-14c.1-.8.7-1.6 1.6-1.8H17c.8.1 1.6.7 1.8 1.6v14.2c-.1.8-.7 1.6-1.6 1.8H3.1c-.8-.1-1.6-.7-1.8-1.6l-.1-.2zm2-8.4v7.4c0 .5.3.7.7.7h12c.5 0 .7-.3.7-.7V8.7h-1.5c.4 1.6.1 3.1-.8 4.5-1 1.3-2.3 2.1-3.9 2.2-1.4.1-2.8-.3-3.9-1.2-1.7-1.5-2.3-3.3-1.8-5.5H3.2zm10.1 1.4c0-1.9-1.5-3.4-3.4-3.4s-3.4 1.5-3.4 3.4 1.5 3.4 3.4 3.4 3.4-1.4 3.4-3.4zm1.8-6.8h-1c-.4 0-.7.3-.7.7v2c0 .4.3.7.7.7h2c.4 0 .7-.3.7-.7V4.1c0-.4-.3-.8-.7-.8h-1z"
                          ></path>
                        </svg>
                      </use>
                    </svg>
                  </v-btn>
                  <v-btn tile class="mx-2" icon>
                    <svg class="j-icon">
                      <use
                        xmlns:xlink="http://www.w3.org/1999/xlink"
                        xlink:href="#icon-pinterest-grey"
                      >
                        <svg
                          id="icon-pinterest-grey"
                          viewBox="0 0 133.2 133.1"
                          fill="#BD081C"
                        >
                          <title>Pinterest</title>
                          <path
                            d="M66.6 0C29.8 0 0 29.8 0 66.6c0 28.2 17.5 52.3 42.3 62-.6-5.3-1.1-13.3.2-19.1 1.2-5.2 7.8-33.1 7.8-33.1s-2-4-2-9.9c0-9.3 5.4-16.2 12-16.2 5.7 0 8.4 4.3 8.4 9.4 0 5.7-3.6 14.3-5.5 22.2-1.6 6.6 3.3 12 9.9 12C84.9 93.9 94 81.4 94 63.4c0-15.9-11.5-27.1-27.8-27.1-18.9 0-30.1 14.2-30.1 28.9 0 5.7 2.2 11.9 5 15.2.5.7.6 1.2.5 1.9-.5 2.1-1.6 6.6-1.8 7.5-.3 1.2-1 1.5-2.2.9-8.3-3.9-13.5-16-13.5-25.8 0-21 15.3-40.3 44-40.3 23.1 0 41 16.5 41 38.4 0 22.9-14.5 41.4-34.5 41.4-6.7 0-13.1-3.5-15.3-7.6 0 0-3.3 12.7-4.1 15.8-1.5 5.8-5.6 13-8.3 17.5 6.2 1.9 12.8 3 19.7 3 36.8 0 66.6-29.8 66.6-66.6C133.2 29.8 103.4 0 66.6 0z"
                          ></path>
                        </svg>
                      </use>
                    </svg>
                  </v-btn>
                  <v-btn tile class="mx-2" icon>
                    <svg class="j-icon">
                      <use
                        xmlns:xlink="http://www.w3.org/1999/xlink"
                        xlink:href="#icon-youtube"
                      >
                        <svg
                          id="icon-youtube"
                          viewBox="0 0 18.76 13.19"
                          fill="#c5382a"
                        >
                          <title>Youtube</title>
                          <path
                            d="M18.57 2.85A4.06 4.06 0 0 0 17.83 1a2.68 2.68 0 0 0-1.88-.81C13.32 0 9.38 0 9.38 0S5.44 0 2.81.19A2.68 2.68 0 0 0 .93 1a4.06 4.06 0 0 0-.74 1.85 28.37 28.37 0 0 0-.19 3v1.46a28.37 28.37 0 0 0 .19 3 4.06 4.06 0 0 0 .74 1.89A3.18 3.18 0 0 0 3 13c1.5.14 6.38.19 6.38.19s3.94 0 6.57-.2a2.68 2.68 0 0 0 1.88-.79 4.06 4.06 0 0 0 .75-1.86 28.41 28.41 0 0 0 .19-3V5.88a28.41 28.41 0 0 0-.2-3.03zM7.44 9V3.76l5.07 2.64z"
                          ></path>
                        </svg>
                      </use>
                    </svg>
                  </v-btn>
                </v-card-text>
              </v-card>
            </div>
          </v-col>
          <v-col>
            <div class="d-flex flex-column align-center">
              <h3 class="mb-2">Наши магазины</h3>
              <div class="d-flex">
                <v-img
                  src="https://www.jacadi.co.uk/medias/sys_master/images/images/h27/hc7/9099826528286/visuel-boutique-2-.jpg"
                ></v-img>
                <div class="ml-2 d-flex flex-column">
                  <span class="grey--text mb-4">
                    Найти Jacadi магазин
                  </span>
                  <v-btn tile color="#8798bf" class="white--text" elevation="0"
                    >Найти</v-btn
                  >
                </div>
              </div>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <v-footer app absolute padless>
      <v-card width="100%" color="#8798bf" class="white--text text-center">
        <v-card-text class="d-flex flex-wrap justify-space-around py-5">
          <nuxt-link to="/" class="white--text px-2">Our group</nuxt-link>
          <span class="white--text">|</span>
          <nuxt-link to="/" class="white--text px-2">
            Conditions of sale</nuxt-link
          >
          <span class="white--text">|</span>
          <nuxt-link to="/" class="white--text px-2"> Terms of use</nuxt-link>
          <span class="white--text">|</span>
          <nuxt-link to="/" class="white--text px-2"> Legal mentions</nuxt-link>
          <span class="white--text">|</span>
          <nuxt-link to="/" class="white--text px-2"> Cookies policy</nuxt-link>
          <span class="white--text">|</span>
          <nuxt-link to="/" class="white--text px-2"> Privacy policy</nuxt-link>
          <span class="white--text">|</span>
          <nuxt-link to="/" class="white--text px-2"> FAQ</nuxt-link>
        </v-card-text>

        <v-divider></v-divider>

        <div
          class="d-none d-lg-block pt-4 white black--text footer-line-height"
        >
          Timelessly elegant and stylish, on the Jacadi Paris website, a wide
          variety of designer children’s clothes and chic
          <a
            href="https://www.jacadi.co.uk/shoes/c/cat-shoes"
            class="grey--text"
            >shoes</a
          >
          awaits little girls and boys. From high quality bodysuits, jumpsuits
          and rompers for
          <a
            href="https://www.jacadi.co.uk/newborn/c/cat-newborn"
            class="grey--text"
            >newborns</a
          >
          to cute dresses, shirts and trousers for
          <a
            href="https://www.jacadi.co.uk/toddler/c/cat-toddler"
            class="grey--text"
            >toddlers</a
          >
          to beautiful cardigans, jumpers, socks and other accessories for
          <a
            href="https://www.jacadi.co.uk/child/c/cat-child"
            class="grey--text"
            >children</a
          >
          from 1 month to 12 years old. Discover our fashion collection for
          girls and boys. Enjoy our collection specially designed for
          <a
            href="https://www.jacadi.co.uk/gift-ideas/christmas"
            class="grey--text"
            >Christmas</a
          >
          and find
          <a
            href="https://www.jacadi.co.uk/Christmas/Gift-ideas/c/cat-christmas-gift-ideas"
            class="grey--text"
            >Christmas gift ideas</a
          >. A happy moment is about to come? Find also our ideas for
          <a
            href="https://www.jacadi.co.uk/gifts-for-newborn"
            class="grey--text"
            >newborn gifts</a
          >. During the
          <a href="https://www.jacadi.co.uk/sale" class="grey--text">sale</a>
          or
          <a href="https://www.jacadi.co.uk/black-friday" class="grey--text"
            >Black Friday</a
          >, you can get baby and children’s clothes, shoes and accessories
          designed by Jacadi for up to 50% off. Find the Jacadi collection
          <a href="https://www.jacadi.co.uk/essentiels" class="grey--text"
            >Les Essentiels</a
          >
          and its emblematic clothes full of Jacadi Paris colours; or the
          <a href="https://www.jacadi.co.uk/little-knits" class="grey--text"
            >Little knits</a
          >
          collection to complete baby’s wardrobe. To face the cold of winter,
          discover our
          <a
            href="https://www.jacadi.co.uk/Winter/c/cat-winter"
            class="grey--text"
            >winter collection</a
          >:
          <a href="https://www.jacadi.co.uk/winter-coats" class="grey--text"
            >outerwear</a
          >, jumpers, hats, tights, scarfs, and more. A wedding, a christening,
          a communion? Discover the
          <a href="https://www.jacadi.co.uk/occasion-wear" class="grey--text"
            >occasion wear outfits</a
          >. Find out also
          <a href="https://www.jacadi.co.uk/tohana" class="grey--text"
            >Tohana</a
          >
          tote bags, manufactured in partnership with Madagascan association
          Tohana and support mothers with no revenues to learn to be
          dressmakers. Order children's clothing from Jacadi
          <a href="https://www.jacadi.co.uk/jacadi-shops" class="grey--text"
            >online</a
          >
          and have your order delivered throughout the UK. Find Jacadi
          recommendations for
          <a
            href="https://www.jacadi.co.uk/care-fine-materials"
            class="grey--text"
            >the care of fine material</a
          >.
        </div>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: null,
      search: null,
      icons: ['mdi-facebook', 'mdi-twitter', 'mdi-linkedin', 'mdi-instagram'],
      firstItems: [
        // {
        //   title: 'Новости',
        //   items: [
        //     { title: 'Liberty' },
        //     { title: 'Essentiels' },
        //     { title: 'School Uniforms' },
        //     { title: 'My first Jacadi' },
        //     { title: 'Особый случай' }
        //   ]
        // },
        {
          title: 'Новинки',
          items: [
            { title: 'Новорожденные' },
            { title: 'Младенцы' },
            { title: 'Дети' },
            { title: 'Обувь' },
            { title: 'Коллекция весна–лето' }
          ]
        }
      ],
      secondItems: [
        {
          title: 'Новорожденные',
          items: [{ title: 'Девочки 1–12 мес' }, { title: 'Мальчики 1–12 мес' }]
        },
        {
          title: 'Младенцы',
          items: [{ title: 'Девочки 6–36 мес' }, { title: 'Мальчики 6–36 мес' }]
        },
        {
          title: 'Дети',
          items: [{ title: 'Девочки 3–12 лет' }, { title: 'Мальчики 3–12 лет' }]
        },
        {
          title: 'Обувь',
          items: [{ title: 'Девочки' }, { title: 'Мальчики' }]
        }
      ],
      itemsNotGroup: [
        // {
        //   title: 'Home',
        //   link: ''
        // },
        {
          title: 'Забота о коже',
          link: ''
        },
        {
          title: 'Комплекты',
          link: ''
        },
        // {
        //   title: 'Подарки новорожденным',
        //   link: ''
        // },
        {
          title: 'История Jacadi',
          link: ''
        }
      ],
      breadcrumbs: [
        {
          text: 'Главная',
          disabled: false,
          href: '/'
        },
        {
          text: 'Дети',
          disabled: false,
          href: '/'
        },
        {
          text: 'Девочки',
          disabled: false,
          href: '/'
        },
        {
          text: 'Купальники',
          disabled: false,
          href: '/'
        },
        {
          text: 'Детская футболка с УФ защитой',
          disabled: true,
          href: '/'
        }
      ]
    }
  }
}
</script>
