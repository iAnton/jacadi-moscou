<template>
  <div>
    <v-row class="d-flex flex-column">
      <v-col>
        <div class="d-none d-md-block mb-4">
          <v-img
            class="mb-6"
            src="https://www.jacadi.co.uk/medias/e20-bann-pageliste-generique.jpg?context=bWFzdGVyfGltYWdlc3w1NjI3fGltYWdlL2pwZWd8aW1hZ2VzL2hlNy9oY2QvOTIzMzIyNDM2ODE1OC5qcGd8OTBkN2NiMjIwMWM2Yzc1ZDExZDVlNGRiMDBiYTJjY2VmMzEyNDY4YmNlMzc1OGQyZmNlN2RhZTEzYjUyYmNiYw"
          >
            <div class="d-flex justify-center align-center fill-height">
              <div class="d-flex flex-column">
                <span>Child girl</span>
                <span class="text-h3">Dresses & skirts</span>
              </div>
            </div>
          </v-img>
          Discover Jacadi's dresses and skirts for 3 to 12-year-old girls: fresh
          Liberty prints dresses, with short or long sleeves and ruffle details,
          pleated or lace trimmed skirts… Elegant and versatile clothes for a
          modern girl wardrobe
        </div>
      </v-col>
      <v-col class="d-flex flex-column flex-md-row align-center border-tb">
        <span class="mr-2">Фильтр:</span>
        <v-select
          v-model="filterSizes"
          class="mr-2 mb-2"
          :items="sizes"
          label="Размер"
          multiple
          hide-selected
          hide-details
          solo
          style="width: 300px"
          no-data-text="Нет фильтров"
        ></v-select>
        <v-select
          v-model="filterColors"
          class="mr-2 mb-2"
          :items="colors"
          return-object
          label="Цвет"
          multiple
          hide-selected
          hide-details
          chips
          solo
          style="width: 300px"
          no-data-text="Нет фильтров"
        >
          <template v-slot:item="{ item }">
            <v-chip :value="item" :color="item.hex" label>
              &nbsp;
            </v-chip>
          </template>
          <template v-slot:selection="{ item }">
            <v-chip :value="item" :color="item.hex" label>
              &nbsp;
            </v-chip>
          </template>
        </v-select>
        <v-select
          v-model="filterGender"
          class="mr-2 mb-2"
          :items="genders"
          label="Пол"
          multiple
          hide-selected
          hide-details
          solo
          style="width: 300px"
          no-data-text="Нет фильтров"
        ></v-select>
        <v-select
          v-model="filterDiscount"
          class="mr-2 mb-2"
          :items="discount"
          label="Скидка"
          multiple
          hide-selected
          hide-details
          solo
          style="width: 300px"
          no-data-text="Нет фильтров"
        ></v-select>
        <v-select
          :items="filterBy"
          class="mr-2 mb-2"
          label="Сортировка"
          hide-details
          solo
          style="width: 300px"
        ></v-select>
      </v-col>
      <v-col class="d-flex flex-column flex-md-row align-center py-6">
        <span class="mr-2 pa-2 pl-0"
          >Найдено {{ alsoItems.length }} вещей:</span
        >
        <v-chip
          v-for="(size, z) in filterSizes"
          :key="z"
          class="mr-2 mb-2"
          close
          label
          @click:close="filterSizes.splice(filterSizes.indexOf(size), 1)"
        >
          {{ size }}
        </v-chip>
        <v-chip
          v-for="(color, j) in filterColors"
          :key="j"
          :color="color.hex"
          class="mr-2 mb-2"
          close
          label
          @click:close="filterColors.splice(filterColors.indexOf(color), 1)"
        >
        </v-chip>
        <v-chip
          v-for="(gender, k) in filterGender"
          :key="k"
          class="mr-2 mb-2"
          close
          label
          @click:close="filterGender.splice(filterGender.indexOf(gender), 1)"
        >
          {{ gender }}
        </v-chip>
        <v-chip
          v-for="(disc, l) in filterDiscount"
          :key="l"
          class="mr-2 mb-2"
          close
          label
          @click:close="filterDiscount.splice(filterDiscount.indexOf(disc), 1)"
        >
          {{ disc }}
        </v-chip>
        <v-chip
          v-if="
            filterSizes.length ||
              filterColors.length ||
              filterGender.length ||
              filterDiscount.length
          "
          class="mr-2 mb-2"
          close
          label
          @click:close="remove"
        >
          Очистить фильтр
        </v-chip>
      </v-col>
      <v-divider></v-divider>
      <v-col class="d-none d-md-flex flex-wrap">
        <v-hover
          v-for="(item, index) in alsoItems"
          :key="index"
          v-slot:default="{ hover }"
          class="mr-8"
        >
          <v-card
            width="300"
            elevation="0"
            class="relative"
            @click="$router.push('/')"
          >
            <v-img aspect-ratio="1" :src="item.src">
              <div class="d-flex justify-space-between pa-2">
                <v-icon>mdi-heart-outline</v-icon>
                <span v-if="item.sale" class="sale-price">-40%</span>
              </div>

              <div class="v-card--reveal white transition-ease-in-out">
                <v-card-title>
                  <v-spacer></v-spacer>
                  {{ item.title }}
                </v-card-title>

                <v-card-subtitle class="d-flex justify-end">
                  <span class="text-decoration-line-through grey--text"
                    >{{ item.price }} р.</span
                  >
                  <span class="ml-2">{{ item.salePrice }} р.</span>
                </v-card-subtitle>

                <v-expand-transition>
                  <div
                    v-if="hover"
                    class="d-flex flex-column transition-ease-in-out"
                  >
                    <div class="mb-4">
                      Размеры в наличии:
                    </div>
                    <div class="d-flex">
                      <div
                        v-for="(size, i) in sizes"
                        :key="i"
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
                        <label :for="size.name">{{ size }}</label>
                      </div>
                    </div>
                  </div>
                </v-expand-transition>
              </div>
            </v-img>
          </v-card>
        </v-hover>
      </v-col>
      <v-col class="grid-wrapper d-md-none">
        <v-hover
          v-for="(item, index) in alsoItems"
          :key="index"
          v-slot:default="{ hover }"
          class="mr-2"
        >
          <v-card elevation="0" class="relative" @click="$router.push('/')">
            <v-img aspect-ratio="1" :src="item.src">
              <div class="d-flex justify-space-between pa-2">
                <v-icon>mdi-heart-outline</v-icon>
                <span v-if="item.sale" class="sale-price">-40%</span>
              </div>

              <div class="v-card--reveal white transition-ease-in-out">
                <v-card-title class="text-body-1">
                  <v-spacer></v-spacer>
                  {{ item.title }}
                </v-card-title>

                <v-card-subtitle class="d-flex text-caption justify-end">
                  <span class="text-decoration-line-through grey--text"
                    >{{ item.price }} р.</span
                  >
                  <span class="ml-2">{{ item.salePrice }} р.</span>
                </v-card-subtitle>

                <v-expand-transition>
                  <div
                    v-if="hover"
                    class="d-flex flex-column transition-ease-in-out"
                  >
                    <div class="mb-4">
                      Размеры в наличии:
                    </div>
                    <div class="d-flex">
                      <div
                        v-for="(size, i) in sizes"
                        :key="i"
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
                        <label :for="size.name">{{ size }}</label>
                      </div>
                    </div>
                  </div>
                </v-expand-transition>
              </div>
            </v-img>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filter: [],
      filteredItems: [],
      filterSizes: [],
      filterColors: [],
      filterGender: [],
      filterDiscount: [],
      filterBy: ['Сначала дешевое', 'Сначала дорогое', 'Новинки'],
      sizes: ['3 Г', '4 Г', '6 Л', '8 Л'],
      colors: [
        {
          text: 'Бледно-розовый',
          hex: '#ffe8e9'
        },
        {
          text: 'Голубой/разноцветный',
          hex: '#10a5f5'
        }
      ],
      genders: ['Мальчик', 'Девочка'],
      discount: ['30 %', '40 %'],
      pickedSize: null,
      alsoItems: [
        {
          title: 'Футболка',
          price: '10.00',
          salePrice: '5.00',
          sale: false,
          src:
            'https://www.hallmark.com/dw/image/v2/AALB_PRD/on/demandware.static/-/Sites-hallmark-master/default/dw53dfd4ab/images/finished-goods/Hi-Im-New-Here-Infant-Bodysuit_1SHT2036_01.jpg?sw=512&sh=512&sm=fit'
        },
        {
          title: 'Футболка',
          price: '20.00',
          salePrice: '10.00',
          sale: false,
          src:
            'https://yolostore.nz/wp-content/uploads/2017/09/vintage-baby-clothes-600x600.png'
        },
        {
          title: 'Футболка',
          price: '15.00',
          salePrice: '10.00',
          sale: true,
          src:
            'https://www.jacadi.co.uk/medias/2022598-895FRONT-product-list?context=bWFzdGVyfGltYWdlc3w1Njc3OHxpbWFnZS9qcGVnfGltYWdlcy9oNGQvaGU3LzkyMzMyNjExMzM4NTQuanBnfGEwNDg1OTJjM2Q3YzYxMzUwODQ4ZGMzMTk5ZmZkODViMTExOWFhMDA0Y2YxZjY5YmY0MDkyNjcxNzEwY2MyNTE'
        },
        {
          title: 'Шорты',
          price: '25.00',
          salePrice: '15.00',
          sale: true,
          src:
            'https://www.jacadi.co.uk/medias/2021627-834FRONT-product-list?context=bWFzdGVyfGltYWdlc3w5NTYyfGltYWdlL2pwZWd8aW1hZ2VzL2g1ZC9oMmUvOTIzMzk4MDcxOTEzNC5qcGd8MmI5OGU5Y2I5MzE4ZjEwNDMwMDYxYzA3MDg3YjU2ZWQ0Mjc2MzdlOWQ1ZGM0MmY3NjNiMDllYWNkZGIwMzg3OA'
        },
        {
          title: 'Шорты',
          price: '25.00',
          salePrice: '15.00',
          sale: true,
          src:
            'https://www.jacadi.co.uk/medias/2021672-895FRONT-product-list?context=bWFzdGVyfGltYWdlc3w2MTQ0M3xpbWFnZS9qcGVnfGltYWdlcy9oZDEvaDkyLzkyMjYyODk2NDM1NTAuanBnfGI1OTA3MjRhNDliMmUzYzJiMzQ1ZmJkZWZjNzU3MWVkMjI4ZTFhZTE0ZjhlZTg4Y2U5OTYzMTc5OGM4NDQ0ZGY'
        }
      ]
    }
  },
  methods: {
    remove() {
      this.filterSizes = []
      this.filterColors = []
      this.filterGender = []
      this.filterDiscount = []
    }
  }
}
</script>

<style>
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  position: absolute;
  width: 100%;
}
</style>
