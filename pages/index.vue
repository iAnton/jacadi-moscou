<template>
  <div>
    <v-row column>
      <v-col cols="12" md="8">
        <div class="d-none d-md-block">
          <v-img v-for="(image, index) in items" :key="index" :src="image.src">
            <div v-if="index === 0" class="d-flex justify-end mr-5 mt-5">
              <span class="sale-price">-40%</span>
            </div>
          </v-img>
        </div>
        <div class="d-block d-md-none">
          <v-carousel hide-delimiter-background>
            <v-carousel-item
              v-for="(carouselItem, index) in items"
              :key="index"
              :src="carouselItem.src"
            >
              <div v-if="index === 0" class="d-flex justify-end mr-5 mt-5">
                <span class="sale-price">-40%</span>
              </div>
              <!-- <v-sheet :color="colors[i]" height="100%">
                <v-row class="fill-height" align="center" justify="center">
                  <div class="display-3">{{ item }} Slide</div>
                </v-row>
              </v-sheet> -->
            </v-carousel-item>
          </v-carousel>
        </div>
      </v-col>
      <v-col cols="12" md="4">
        <v-card elevation="0" class="sticky">
          <v-card-title class="headline mb-8">
            {{ article.title }}
          </v-card-title>
          <v-card-text class="pb-0">
            <v-divider></v-divider>
            <v-row class="d-flex mt-4">
              <v-col
                class="d-flex align-center pointer"
                @click="openDescription"
              >
                Описание<v-icon v-if="!opened.description">mdi-plus</v-icon
                ><v-icon v-else>mdi-minus</v-icon>
              </v-col>
              <v-col
                class="d-flex align-center pointer"
                @click="openComposition"
              >
                Состав<v-icon v-if="!opened.composition">mdi-plus</v-icon
                ><v-icon v-else>mdi-minus</v-icon>
              </v-col>
            </v-row>
            <div v-if="opened.description">
              {{ article.description }}
            </div>
            <div v-if="opened.composition">
              <div class="mb-8">
                Основа:<br />{{ article.composition.main }}<br />
              </div>
              <div>
                Инструкция по уходу:<br />
                <svg class="j-icon" title="Machine washable even at 30º">
                  <use xlink:href="#icon-entretien-0">
                    <svg id="icon-entretien-0" viewBox="0 0 264 235.2">
                      <title>entretien-3</title>
                      <path
                        d="M92.7 167.2c-7.3 0-13.5-1.6-18.5-4.8-5-3.2-8.3-7.6-9.8-13.2l7.3-8.5c.2 1.5.7 3 1.8 4.7 1 1.7 2.4 3.2 4.1 4.6 1.7 1.4 3.9 2.5 6.4 3.5 2.5.9 5.3 1.4 8.5 1.4 2.5 0 4.9-.3 7-.9 2.2-.6 4.1-1.5 5.7-2.7 1.6-1.2 2.9-2.6 3.8-4.2.9-1.6 1.4-3.5 1.4-5.6 0-4.6-2.3-8.1-6.9-10.5-4.6-2.3-10.9-3.5-19-3.5h-4.1v-11.3h4.1c7 0 12.8-1.1 17.1-3.2 4.4-2.1 6.6-5.4 6.6-9.8 0-2-.4-3.8-1.3-5.4-.9-1.6-2.1-2.9-3.5-4-1.5-1.1-3.1-1.9-4.9-2.4-1.8-.5-3.7-.8-5.5-.8-5.1 0-9.3 1.1-12.7 3.3-3.4 2.2-5.7 4.7-7.1 7.5l-8.8-9.6c1.3-2 3-3.8 5-5.5 2.1-1.6 4.4-3 6.9-4.1 2.5-1.1 5.2-1.9 8-2.6 2.8-.6 5.7-.9 8.5-.9 4.2 0 8.1.6 11.8 1.8 3.6 1.2 6.8 2.9 9.4 5 2.6 2.1 4.6 4.7 6.1 7.5 1.5 2.9 2.2 6 2.2 9.4 0 4.9-1.4 8.9-4.3 12-2.9 3.2-6.9 5.3-12.2 6.6 2.8.5 5.4 1.4 7.7 2.8s4.2 3 5.8 5c1.6 1.9 2.9 4.2 3.7 6.6.9 2.5 1.3 5 1.3 7.7 0 3.9-.9 7.3-2.7 10.3-1.8 3-4.1 5.5-7 7.5-2.9 2-6.3 3.5-10.1 4.6-3.9 1.2-7.8 1.7-11.8 1.7zm79.7.1c-6.1-.1-11.4-1.5-16-4.3s-8.5-6.2-11.5-10.5c-3.1-4.2-5.4-8.9-7-14-1.6-5.1-2.4-10.1-2.4-15 0-5.2.9-10.4 2.6-15.6 1.7-5.2 4.2-9.9 7.4-14.1 3.2-4.2 7.1-7.6 11.6-10.1 4.5-2.6 9.7-3.9 15.4-3.9 6.1 0 11.4 1.4 16 4.2 4.6 2.8 8.4 6.3 11.5 10.6 3.1 4.3 5.4 9 7 14.2 1.5 5.1 2.3 10.1 2.3 14.8 0 5.3-.9 10.5-2.6 15.7-1.7 5.2-4.2 9.8-7.4 14a40.1 40.1 0 0 1-11.6 10.1c-4.5 2.5-9.6 3.8-15.3 3.9zm-23.1-43.8c.1 3.6.6 7.4 1.6 11.1 1 3.8 2.5 7.2 4.4 10.1 1.9 3 4.3 5.5 7.1 7.4 2.8 1.9 6.2 2.9 10 2.9 4 0 7.4-1 10.3-3 2.9-2 5.2-4.6 7.1-7.7 1.9-3.1 3.3-6.5 4.2-10.2.9-3.7 1.4-7.3 1.4-10.6 0-3.6-.5-7.4-1.5-11.1-1-3.8-2.5-7.2-4.4-10.1-1.9-3-4.3-5.4-7.2-7.4-2.8-1.9-6.1-2.9-9.8-2.9-4 0-7.4 1-10.3 3-2.9 2-5.3 4.6-7.2 7.7-1.9 3.1-3.3 6.5-4.2 10.2-1 3.8-1.5 7.3-1.5 10.6z"
                      ></path>
                      <path
                        d="M247.7 38.6L243.3 60c-8.5-1.3-13.6-5.1-19.2-9.4-7.6-5.7-16.2-12.2-32.7-12.2-16.6 0-25.2 6.5-32.7 12.2-7 5.3-13 9.8-25.5 9.8-12.6 0-18.6-4.5-25.5-9.8-7.8-5.6-16.4-12.1-33-12.1-16.5 0-25.1 6.5-32.7 12.2-5.8 4.4-11 8.4-19.9 9.6l-4.7-23H1l32.9 161h197l33-159.5-16.2-.2zM218 182.2H47L24.5 72.1c11.5-1.7 18.5-7 24.8-11.7 7-5.3 13-9.8 25.5-9.8 12.6 0 18.6 4.5 25.5 9.8 7.6 5.7 16.2 12.2 32.7 12.2 16.6 0 25.2-6.5 32.7-12.2 7-5.3 13-9.8 25.5-9.8 12.6 0 18.6 4.5 25.5 9.8 6.1 4.6 12.9 9.9 24 11.7L218 182.2z"
                      ></path>
                    </svg>
                  </use>
                </svg>
                <svg class="j-icon" title="Do not bleach">
                  <use xlink:href="#icon-entretien-8">
                    <svg id="icon-entretien-8" viewBox="0 0 269.2 278">
                      <title>entretien-22</title>
                      <path
                        d="M262.5 237L194 118.4l55.3-57.8-11.6-11.1-52.1 54.5L134 14.5l-50.9 88.2-50.9-53.2-11.6 11.1 54.1 56.6L5.5 237h52.8l-23.6 24.7 11.6 11.1L80.5 237h109l34.2 35.8 11.6-11.1-23.7-24.7h50.9zm-31.2-18h-36.9L146 168.5l35-36.5 50.3 87zM134 50.5l38.7 67-37.7 39.4-38.9-40.7L134 50.5zM36.7 219l51-88.3 36.2 37.8L75.5 219H36.7zm61 0l37.3-39 37.3 39H97.7z"
                      ></path>
                    </svg>
                  </use>
                </svg>
                <svg class="j-icon" title="Do not tumble dry">
                  <use xlink:href="#icon-entretien-16">
                    <svg id="icon-entretien-16" viewBox="0 0 294.7 296.3">
                      <title>entretien-26</title>
                      <path
                        d="M259.7 35.3v226h-226v-226h226m20-20h-266v266h266v-266z"
                      ></path>
                      <path
                        d="M147 75.8c40 0 72.5 32.5 72.5 72.5S187 220.8 147 220.8s-72.5-32.5-72.5-72.5S107 75.8 147 75.8m0-20c-51.1 0-92.5 41.4-92.5 92.5s41.4 92.5 92.5 92.5 92.5-41.4 92.5-92.5-41.4-92.5-92.5-92.5z"
                      ></path>
                      <path
                        d="M279.7 26.4l14.6-14.6L283 .5l-14.8 14.8H25.6L10.8.5-.5 11.8 13.7 26v243.8L-.5 284l11.3 11.3 14-14H269l14 14 11.3-11.3-14.6-14.6v-243zm-20 223l-41.8-41.8c13.4-16.1 21.5-36.7 21.5-59.3 0-22.7-8.2-43.6-21.8-59.7l42.1-42.1v202.9zM135.6 147.9l-45.4 45.4c-9.9-12.4-15.8-28-15.8-45.1 0-17.2 6-33 16.1-45.4l45.1 45.1zm-33.8-56.4c12.4-9.9 28-15.8 45.1-15.8 17 0 32.7 5.9 45.1 15.8l-45.1 45.1-45.1-45.1zm45.1 67.7l45.4 45.4c-12.4 10-28.2 16.1-45.4 16.1s-33-6-45.4-16.1l45.4-45.4zm11.3-11.3l45.1-45.1c10 12.4 16.1 28.2 16.1 45.4 0 17-5.9 32.7-15.8 45.1l-45.4-45.4zm90-112.6l-42 42c-16.1-13.4-36.7-21.5-59.3-21.5-22.6 0-43.3 8.1-59.3 21.5l-42-42h202.6zM33.7 46l42.5 42.5c-13.6 16.1-21.8 36.9-21.8 59.7 0 22.6 8.1 43.3 21.5 59.3l-42.2 42.2V46zm11.1 215.3l42.4-42.4c16.1 13.6 36.9 21.8 59.7 21.8 22.7 0 43.6-8.2 59.7-21.8l42.4 42.4H44.8z"
                      ></path>
                    </svg>
                  </use>
                </svg>
                <svg class="j-icon" title="Do not iron">
                  <use xlink:href="#icon-entretien-12">
                    <svg id="icon-entretien-12" viewBox="0 0 269.2 278">
                      <title>entretien-19</title>
                      <path
                        d="M269.5 205L228.2 59H212l42.5-47.9-12-10.6L190.6 59H89.3L37.4.5l-12 10.6L67.9 59H53v19h31.8l43.5 49H81c-46.6 0-76.2 53-79.5 59H1v19h60.1l-21.6 24.4 12 10.6 31-35h114.9l31 35 12-10.6-21.6-24.4h50.7zm-38.1-65l13 46H202l-40.8-46h70.2zm-57.6-62L140 116.1 106.2 78h67.6zm21.4 0h18.6l13.9 49h-76l43.5-49zM16.6 186c8.9-14 32.7-46 64.4-46h37.8L78 186H16.6zm82.8 0l40.6-45.8 40.6 45.8H99.4z"
                      ></path>
                    </svg>
                  </use>
                </svg>
                <svg class="j-icon" title="Do not dry clean">
                  <use xlink:href="#icon-entretien-14">
                    <svg id="icon-entretien-14" viewBox="0 0 294.7 296.3">
                      <title>entretien-29</title>
                      <path
                        d="M281 149.6c0-34.4-13-65.8-34.3-89.6l22.2-22.2-11.3-11.3-22.2 22.2c-23.6-20.8-54.6-33.4-88.5-33.4-34.2 0-65.4 12.8-89 33.8L35.1 26.5 23.8 37.9l22.7 22.7c-21 23.7-33.8 54.9-33.8 89.1 0 33.9 12.6 64.9 33.4 88.5l-22.2 22.2 11.3 11.3 22.2-22.2c23.8 21.3 55.2 34.3 89.6 34.3 34.2 0 65.4-12.8 89.1-33.8l21.7 21.7 11.3-11.3-21.7-21.7c20.8-23.7 33.6-54.9 33.6-89.1zm-20 0c0 27.8-9.9 54.1-28 74.9l-53.2-53.2c1.6-.5 3.2-1.2 4.8-1.9 5.3-2.6 9.8-6 13.6-10.3 3.8-4.3 6.7-9.1 8.7-14.6 2.1-5.5 3.1-11.2 3.1-17 0-5.6-1.1-11.1-3.3-16.6-1-2.6-2.2-5-3.6-7.3l29.4-29.4c18.4 20.9 28.5 47.4 28.5 75.4zm-126-.5l-.4.4v-.8l.4.4zm-.3-23v-20.7h29.8c2.3 0 4.6.4 6.9 1.4 1.4.6 2.6 1.3 3.8 2.3l-28.8 28.8-11.7-11.8zm22.9 22.8l25-24.9c.1 1.1.2 2.3.2 3.5 0 6.9-1.6 12.1-4.9 16.1-3.3 4-7.4 5.8-12.3 5.8h-7.3l-.7-.5zM146.8 35.4c27.6 0 53.7 9.7 74.4 27.5l-28.5 28.5c-2.7-2.2-5.7-4.3-8.9-5.9-5.4-2.6-11.2-4.2-17.6-4.2h-58.5v18L71.9 63.4c20.7-18.1 47.1-28 74.9-28zM32.6 149.6c0-27.8 9.8-54.1 27.9-74.9l47.1 47.2v54.4L60.1 224c-17.8-20.7-27.5-46.8-27.5-74.4zm114.2 114.2c-28.1 0-54.6-10.1-75.5-28.5l36.4-36.4v20.4h27v-46h24.5l62.6 62.5c-20.9 18.2-47.2 28-75 28z"
                      ></path>
                    </svg>
                  </use>
                </svg>
              </div>
            </div>
            <v-divider class="my-4"></v-divider>
            <div class="mb-4">
              <div class="mb-2">
                Цвет: <b>{{ pickedColor }}</b>
              </div>
              <div class="radio-colors d-flex">
                <div
                  v-for="(color, index) in article.colors"
                  :key="index"
                  class="mr-2"
                >
                  <input
                    :id="index"
                    v-model="pickedColor"
                    type="radio"
                    :value="color.name"
                  />
                  <label
                    :for="index"
                    :style="{ backgroundColor: color.hex }"
                  ></label>
                </div>
              </div>
            </div>
            <div class="mb-8">
              <div class="d-flex justify-space-between">
                <div class="mb-2">
                  Размер: <b>{{ pickedSize }}</b>
                </div>
                <nuxt-link to="/">Гид по размерам</nuxt-link>
              </div>
              <div class="d-flex">
                <div
                  v-for="(size, index) in article.sizes"
                  :key="index"
                  class="radio-sizes mr-2"
                  :class="{ 'radio-sizes--disabled': size.disabled }"
                >
                  <input
                    :id="size.name"
                    v-model="pickedSize"
                    type="radio"
                    :value="size.name"
                    :disabled="size.disabled"
                  />
                  <label :for="size.name">{{ size.name }}</label>
                </div>
              </div>
            </div>
            <p class="mb-0 red--text text-decoration-line-through">
              {{ article.price }} ₽
            </p>
            <p class="text-h5 mb-0 black--text">{{ article.salePrice }} ₽</p>
          </v-card-text>
          <v-card-actions>
            <v-row class="d-flex flex-column">
              <v-col>
                <v-btn
                  color="#8798bf"
                  class="white--text btn-cart btn-text-initial"
                  nuxt
                  to="/"
                  tile
                  block
                  elevation="0"
                >
                  В корзину
                </v-btn>
              </v-col>
              <v-col>
                <v-btn text block class="btn-text-initial">
                  <v-icon left>mdi-heart-outline</v-icon> В избранное
                </v-btn>
              </v-col>
            </v-row>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <!-- <v-row class="d-flex flex-column mb-4">
      <v-col class="text-center"><h3>Вам также может понравится</h3></v-col>
      <v-col class="d-flex justify-space-between">
        <v-card class="mx-auto" max-width="300">
          <v-img
            src="https://www.hallmark.com/dw/image/v2/AALB_PRD/on/demandware.static/-/Sites-hallmark-master/default/dw53dfd4ab/images/finished-goods/Hi-Im-New-Here-Infant-Bodysuit_1SHT2036_01.jpg?sw=512&sh=512&sm=fit"
            height="200px"
          ></v-img>

          <v-card-title>
            Название товара
          </v-card-title>

          <v-card-subtitle>
            Цена: 100 руб
          </v-card-subtitle>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="gray" text>
              Посмотреть
            </v-btn>
          </v-card-actions>
        </v-card>
        <v-card class="mx-auto" max-width="300">
          <v-img
            src="https://yolostore.nz/wp-content/uploads/2017/09/vintage-baby-clothes-600x600.png"
            height="200px"
          ></v-img>

          <v-card-title>
            Название товара
          </v-card-title>

          <v-card-subtitle>
            Цена: 100 руб
          </v-card-subtitle>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="gray" text>
              Посмотреть
            </v-btn>
          </v-card-actions>
        </v-card>
        <v-card class="mx-auto" max-width="300">
          <v-img
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcT1vBvWodFO381qFugKl8ctyQ5gyfIpBzEjAunV4NZpoXaHBXox&usqp=CAU"
            height="200px"
          ></v-img>

          <v-card-title>
            Название товара
          </v-card-title>

          <v-card-subtitle>
            Цена: 100 руб
          </v-card-subtitle>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="gray" text>
              Посмотреть
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <v-divider></v-divider>
    <v-row>
      <v-col class="d-flex justify-space-around">
        <div class="d-flex align-center">
          <v-icon class="pa-4">mdi-phone</v-icon>
          <div class="d-flex flex-column">
            <span>Поддержка</span>
            <nuxt-link to="/">Подробнее</nuxt-link>
          </div>
        </div>
        <div class="d-flex align-center">
          <v-icon class="pa-4">mdi-sync</v-icon>
          <div class="d-flex flex-column">
            <span>Бесплатный возврат товара</span>
            <nuxt-link to="/">Подробнее</nuxt-link>
          </div>
        </div>
        <div class="d-flex align-center">
          <v-icon class="pa-4">mdi-train-car</v-icon>
          <div class="d-flex flex-column">
            <span>Бесплатная доставка</span>
            <nuxt-link to="/">Подробнее</nuxt-link>
          </div>
        </div>
        <div class="d-flex align-center">
          <v-icon class="pa-4">mdi-lock</v-icon>
          <div class="d-flex flex-column">
            <span>Защищенные платежи</span>
            <nuxt-link to="/">Подробнее</nuxt-link>
          </div>
        </div>
      </v-col>
    </v-row>
    <v-divider></v-divider>
    <v-row>
      <v-col class="d-flex justify-space-around">
        <div class="d-flex flex-column align-center">
          <h3 class="mb-2">Подписаться на рассылку</h3>
          <v-text-field label="E-mail" outlined></v-text-field>
          <v-btn color="light-blue accent-2">Подписаться</v-btn>
        </div>
        <div class="d-flex flex-column align-center">
          <h3 class="mb-2">Наши магазины</h3>
          <span class="grey--text mb-4">
            Найти ближайшие магазины в вашем городе
          </span>
          <v-btn color="light-blue accent-2">Найти</v-btn>
        </div>
      </v-col>
    </v-row> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      article: {
        title: 'Детская футболка с УФ защитой для девочки',
        description: `В УФ-блокирующем материале, который защитит ее кожу от солнца,
                      эта пляжная футболка с защитой от ультрафиолета изготовлена из микрофибры и
                      эластан. Приподнятый контрастным лепестковым воротником, он имеет липучку
                      застежка сзади для удобства ношения. Эта футболка была разработана для
                      купание на пляже или в бассейне, а также можно носить с плаванием
                      плавки или купальник из двух частей. Предупреждение: должен сопровождаться
                      шляпой, солнцезащитными очками и адекватной защитой от ультрафиолета на всех открытых
                      кожа.`,
        composition: {
          main: '91% полиамид, 9% эластан',
          care: {}
        },
        colors: [
          {
            name: 'Бледно-розовый',
            hex: '#ffe8e9'
          },
          {
            name: 'Голубой/разноцветный',
            hex: '#10a5f5'
          }
        ],
        sizes: [
          {
            name: '3 Г',
            disabled: true
          },
          {
            name: '4 Г',
            disabled: false
          },
          {
            name: '6 Л',
            disabled: false
          },
          {
            name: '8 Л',
            disabled: true
          }
        ],
        price: '3 399',
        salePrice: '1 649'
      },
      pickedColor: null,
      pickedSize: null,
      items: [
        {
          src:
            'https://www.jacadi.co.uk/medias/sys_master/images/images/h6b/h04/9233060593694/2021304-830FRONT-product.jpg'
        },
        {
          src:
            'https://www.jacadi.co.uk/medias/sys_master/images/images/h83/h60/9233062232094/2021304-830BACK-product.jpg'
        },
        {
          src:
            'https://www.jacadi.co.uk/medias/sys_master/images/images/h43/h5e/9233061576734/2021304-830JSV02-product.jpg'
        },
        {
          src:
            'https://www.jacadi.co.uk/medias/sys_master/images/images/hab/h98/9233055678494/2021304-830JSV03-product.jpg'
        }
      ],
      opened: {
        description: false,
        composition: false
      }
    }
  },
  methods: {
    openDescription() {
      this.opened.description = !this.opened.description
      this.opened.composition = false
    },
    openComposition() {
      this.opened.description = false
      this.opened.composition = !this.opened.composition
    }
  }
}
</script>

<style></style>
