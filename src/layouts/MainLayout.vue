<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          <div class="flex flex-center">
            <img
            alt="fanadewi logo"
            src="~assets/fanadewi.svg"
            style="width:40px"
            >
          fanadewi
          </div>
        </q-toolbar-title>

        <div>{{ new Date().toJSON().slice(0,10).replace(/-/g,'/') }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Menu
        </q-item-label>
        <Menu
          v-for="link in menuLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import Menu from 'components/Menu.vue'

const menuLinks = [
  {
    title: 'Github',
    caption: 'github.com/fanadewi',
    icon: 'code',
    link: 'https://github.com/fanadewi'
  },
  {
    title: 'Twitter',
    caption: '@myfanadewi',
    icon: 'rss_feed',
    link: 'https://twitter.com/myfanadewi'
  },
  {
    title: 'Medium',
    caption: 'fanadewi.medium.com',
    icon: 'favorite',
    link: 'https://fanadewi.medium.com'
  }
];

export default {
  name: 'MainLayout',
  components: { Menu },
  data () {
    return {
      leftDrawerOpen: false,
      menuLinks: menuLinks
    }
  }
}
</script>
