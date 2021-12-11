<template>
  <nav>
    <v-app-bar app flat>
      <v-app-bar-nav-icon @click="drawer = !drawer" />

      <nuxt-link :to="title.to" tag="div" class="cp">
        <v-app-bar-title class="grey--text text-uppercase">
          {{ title.first }}
          <span class="font-weight-bold">{{ title.second }}</span>
        </v-app-bar-title>
      </nuxt-link>

      <v-spacer />

      <v-menu offset-y>
        <template #activator="{ on, attrs }">
          <v-btn text color="grey" v-bind="attrs" v-on="on">
            <v-icon left>
              {{ menu.icon }}
            </v-icon>
            <span class="font-weight-bold">{{ menu.text }}</span>
          </v-btn>
        </template>

        <v-list elevation="0">
          <v-list-item v-for="nav of navigations" :key="nav.text" :to="nav.to">
            <v-list-item-content>
              <v-list-item-title>
                {{ nav.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-btn text color="grey" :to="signout.to">
        <span class="font-weight-bold">{{ signout.text }}</span>
        <v-icon right>
          {{ signout.icon }}
        </v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" dark app color="indigo lighten-1" class="py-5">
      <div class="text-center">
        <div>
          <v-avatar :size="user.imgSize" class="mb-3">
            <v-img :src="user.img" :alt="user.alt" />
          </v-avatar>
        </div>
        <div>
          <h1 class="text-h6 font-weight-bold white--text">
            {{ user.name }}
          </h1>
        </div>
      </div>

      <v-list>
        <v-list-item v-for="nav of navigations" :key="nav.title" :to="nav.to">
          <v-list-item-icon>
            <v-icon>{{ nav.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title class="font-weight-bold">
              {{ nav.text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import img from '@/assets/avatar-1.png'

export default {
  data () {
    return {
      drawer: false,
      title: {
        first: 'todo',
        second: 'ninja',
        to: '/'
      },
      menu: {
        text: 'メニュー',
        icon: 'mdi-chevron-down'
      },
      signout: {
        text: 'サインアウト',
        icon: 'mdi-logout-variant',
        to: '/signout'
      },
      navigations: [
        { text: 'ダッシュボード', icon: 'mdi-view-dashboard', to: '/' },
        { text: 'プロジェクト一覧', icon: 'mdi-folder', to: '/projects' },
        { text: 'チーム', icon: 'mdi-account', to: '/team' }
      ],
      user: {
        name: 'The Net Ninja',
        alt: 'ユーザー画像',
        imgSize: 100,
        img
      }
    }
  }
}
</script>

<style scoped>
.cp {
  cursor: pointer;
}
</style>
