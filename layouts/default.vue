<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item link @click="$router.push('/')">
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Главная</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-new-box</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Новые поступления</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-percent</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Распродажа</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-information</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>О нас</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="light-blue accent-2" class="white--text">
      <v-app-bar-nav-icon
        class="white--text"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-toolbar-title class="mr-2">Название компании</v-toolbar-title>
      <div>
        <span>Логотип</span>
        <!-- <v-img
          src="https://media.istockphoto.com/vectors/baby-shop-logo-detailed-illustration-vector-id950062114?k=6&m=950062114&s=170667a&w=0&h=m-jDaC_ns5VMyyGHiyUf9j7f9QztbrTkOo6Vs3i0vDE="
          max-height="100"
          contain
        ></v-img> -->
      </div>
      <v-text-field
        class="mx-4"
        flat
        hide-details
        prepend-inner-icon="search"
        solo
      ></v-text-field>
      <nuxt-link class="d-flex flex-column mx-2" to="/">
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
      </nuxt-link>
    </v-app-bar>

    <v-main>
      <v-breadcrumbs :items="items">
        <template v-slot:divider>
          <v-icon>mdi-chevron-right</v-icon>
        </template>
      </v-breadcrumbs>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer app absolute padless>
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
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      icons: ['mdi-facebook', 'mdi-twitter', 'mdi-linkedin', 'mdi-instagram'],
      items: [
        {
          text: 'Главная',
          disabled: false,
          href: '/'
        },
        {
          text: 'Одежда',
          disabled: false,
          href: '/'
        },
        {
          text: 'Футболки',
          disabled: true,
          href: '/'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
a {
  text-decoration: none;
  color: white;
}
</style>
