<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app disable-resize-watcher>
      <v-list dense>
        <v-list-item @click="!drawer">
          <v-list-item-content>
            <v-list-item-title>FAQ Covid-19</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item @click="!drawer">
          <v-list-item-content>
            <v-list-item-title>#stayathome</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-group
          v-for="item in firstItems"
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
        <v-list-item @click="!drawer">
          <v-list-item-content>
            <v-list-item-title>Sale</v-list-item-title>
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
    <v-app-bar app color="#8798bf" class="white--text" elevation="0">
      <v-container>
        <v-row class="">
          <v-col sm="auto">
            <v-app-bar-nav-icon
              class="d-block d-lg-none white--text"
              @click.stop="drawer = !drawer"
            ></v-app-bar-nav-icon
          ></v-col>
          <v-col>
            <nuxt-link class="white--text mr-4" to="/">Jacadi Москва</nuxt-link>
            <!-- <nuxt-link class="white--text" to="/">The e-gift card</nuxt-link> -->
          </v-col>
          <v-spacer></v-spacer>
          <!-- <v-col>
            <nuxt-link class="white--text" to="/"
              >The eshop is open, check our FAQ ></nuxt-link
            >
          </v-col> -->
        </v-row>
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
      </v-container>
    </v-app-bar>

    <v-main>
      <v-container>
        <v-row class="mb-6" no-gutters>
          <v-col class="d-none d-lg-block" cols="2">
            <div class="sticky">
              <v-img
                src="https://www.jacadi.co.uk/_ui/desktop/assets/img/jacadi-logo-without-crown.svg"
                width="139"
              ></v-img>
              <v-navigation-drawer floating permanent>
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
                            'font-weight-bold': item.title === 'Новинки'
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
                        <v-list-item-title
                          v-text="subItem.title"
                        ></v-list-item-title>
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
                        <v-list-item-title
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
                        <v-list-item-title
                          v-text="subItem.title"
                        ></v-list-item-title>
                      </v-list-item-content>
                    </v-list-item>
                  </v-list-group>
                  <v-list-item
                    v-for="item in itemsNotGroup"
                    :key="item.title"
                    @click="$router.push('/')"
                  >
                    <v-list-item-content>
                      <v-list-item-title
                        v-text="item.title"
                      ></v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-navigation-drawer>
            </div>
          </v-col>
          <v-col cols="10">
            <v-breadcrumbs :items="breadcrumbs">
              <template v-slot:divider>
                <v-icon>mdi-chevron-right</v-icon>
              </template>
            </v-breadcrumbs>
            <nuxt />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <!-- <v-footer app absolute padless>
      <v-card
        width="100%"
        flat
        tile
        class="light-blue accent-2 lighten-1 white--text text-center"
      >
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4 white--text"
            icon
          >
            <v-icon size="24px">{{ icon }}</v-icon>
          </v-btn>
        </v-card-text>

        <v-spacer></v-spacer>

        <v-card-text class="d-flex justify-space-around white--text pt-0">
          <nuxt-link to="/">О нас</nuxt-link>
          <nuxt-link to="/">Контакты</nuxt-link>
          <nuxt-link to="/">Политика конфиденциальности</nuxt-link>
          <nuxt-link to="/">Условия использования</nuxt-link>
          <nuxt-link to="/">Часто задаваемые вопросы</nuxt-link>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} —
          <strong>Интернет-магазин детских вещей</strong>
        </v-card-text>
      </v-card>
    </v-footer>
    <v-footer>
      <v-spacer></v-spacer>
      <div>&copy; {{ new Date().getFullYear() }}</div>
    </v-footer> -->
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
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
