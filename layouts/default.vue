<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-layout justify-space-between column fill-height>
        <v-list>
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :to="item.to"
            router
            exact
          >
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>
        </v-list>
        <div justify-end class="pa-4">
          <v-btn
            v-if="theme == 'dark'"
            block
            rounded
            elevation="0"
            @click="changeTheme('light')"
          >
            <v-icon>mdi-weather-night</v-icon>
            Dark
          </v-btn>
          <v-btn
            v-else
            block
            rounded
            elevation="0"
            @click="changeTheme('dark')"
          >
            <v-icon>mdi-weather-sunny</v-icon>
            Light
          </v-btn>
        </div>
      </v-layout>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <nuxt-link to="/">
        <v-img src="/logo.png" max-width="48px"></v-img>
      </nuxt-link>
      <nuxt-link
        to="/"
        style="text-decoration: none; font-size: 120%"
        :class="this.$vuetify.theme.dark ? 'white--text' : 'black--text'"
      >
        {{ $t('chapter') }}
      </nuxt-link>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="false" app>
      <span>&copy; {{ new Date().getFullYear() }} {{ $t('chapter') }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      items: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/',
        },
        {
          icon: 'mdi-ticket',
          title: 'Events',
          to: '/events',
        },
        {
          icon: 'mdi-account-group-outline',
          title: 'Team',
          to: '/team',
        },
        {
          icon: 'mdi-progress-question',
          title: 'About',
          to: '/about',
        },
      ],
      miniVariant: false,
      title: 'Vuetify.js',
      theme: 'dark',
    }
  },
  watch: {
    theme(newValue) {
      switch (newValue) {
        case 'light':
          this.$vuetify.theme.dark = false
          break
        default:
          this.$vuetify.theme.dark = true
          break
      }
    },
  },
  mounted() {
    if (localStorage.theme !== null) {
      this.theme = localStorage.theme
    }
  },
  methods: {
    changeTheme(newTheme) {
      this.theme = newTheme
      localStorage.theme = newTheme
    },
  },
}
</script>
