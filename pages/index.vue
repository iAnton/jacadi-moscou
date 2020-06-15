<template>
  <div>
    <v-row column>
      <v-col cols="12" sm="6" md="8">
        <v-card>
          <v-card-title class="headline">
            Футболка
          </v-card-title>
          <v-card-text>
            <v-carousel
              cycle
              height="400"
              hide-delimiter-background
              show-arrows-on-hover
            >
              <v-carousel-item v-for="(slide, i) in slides" :key="i">
                <v-sheet :color="colors[i]" height="100%">
                  <v-row class="fill-height" align="center" justify="center">
                    <div class="display-3">{{ slide }}</div>
                  </v-row>
                </v-sheet>
              </v-carousel-item>
            </v-carousel>
          </v-card-text>
          <v-card-actions>
            <v-spacer />
            <v-btn color="light-blue accent-2" class="white--text" nuxt to="/">
              Купить
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="6" md="4">
        <v-card>
          <v-card-title class="headline">
            Футболка
          </v-card-title>
          <v-card-text>
            <v-expansion-panels accordion class="mb-2">
              <v-expansion-panel>
                <v-expansion-panel-header>Описание</v-expansion-panel-header>
                <v-expansion-panel-content>
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                  do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco
                  laboris nisi ut aliquip ex ea commodo consequat.
                </v-expansion-panel-content>
              </v-expansion-panel>
              <v-expansion-panel>
                <v-expansion-panel-header>Состав</v-expansion-panel-header>
                <v-expansion-panel-content>
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                  do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco
                  laboris nisi ut aliquip ex ea commodo consequat.
                </v-expansion-panel-content>
              </v-expansion-panel>
            </v-expansion-panels>
            <div class="mb-2">
              <span>Цвет:</span>
              <v-item-group class="mt-2" mandatory>
                <v-item
                  v-for="color in colors"
                  :key="color"
                  v-slot:default="{ active, toggle }"
                >
                  <v-chip
                    :active-class="color"
                    :input-value="active"
                    @click="toggle"
                  >
                    {{ color }}
                  </v-chip>
                </v-item>
              </v-item-group>
            </div>
            <div class="mb-4">
              <span>Размер:</span>
              <v-item-group mandatory class="mt-2">
                <v-item
                  v-for="size in sizes"
                  :key="size"
                  v-slot:default="{ active, toggle }"
                >
                  <v-chip
                    active-class="light-blue accent-2"
                    :input-value="active"
                    @click="toggle"
                  >
                    {{ size }}
                  </v-chip>
                </v-item>
              </v-item-group>
            </div>
            <div class="mb-2">Цена: <b>100 руб.</b></div>
          </v-card-text>
          <v-card-actions>
            <v-spacer />
            <v-btn color="light-blue accent-2" class="white--text">
              <v-icon>mdi-heart</v-icon>
            </v-btn>
            <v-btn color="light-blue accent-2" class="white--text" nuxt to="/">
              Добавить в корзину
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <v-row class="d-flex flex-column mb-4">
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
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      colors: ['red', 'blue', 'green', 'yellow', 'pink'],
      sizes: ['xs', 's', 'm', 'l', 'xl'],
      slides: ['1', '2', '3', '4', '5']
    }
  }
}
</script>
