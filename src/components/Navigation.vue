<template>
  <v-navigation-drawer v-model="show" absolute right temporary>
    <v-list-item>
      <v-list-item-avatar>
        <v-img :src="profileImage"></v-img>
      </v-list-item-avatar>

      <v-list-item-content>
        <v-list-item-title>Fabian Bolte</v-list-item-title>
      </v-list-item-content>
    </v-list-item>

    <v-divider></v-divider>

    <v-list dense>
      <v-list-item v-for="page in pages" :key="page.name" :to="page.link" link>
        <v-list-item-icon>
          <v-icon>{{ page.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ page.name }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
import { mdiHome, mdiBookOpenVariant, mdiNewspaper, mdiPresentation, mdiInformationVariant } from '@mdi/js'
export default {
  props: {
    showNav: {
      type: Boolean,
      default: false
    }
  },
  data: () => ({
    show: false,
    profileImage: require('../../assets/images/profile-160x160.jpg'),
    pages: [
      {
        name: 'Home',
        icon: mdiHome,
        link: '/'
      },
      {
        name: 'Portfolio',
        icon: mdiBookOpenVariant,
        link: '/portfolio'
      },
      {
        name: 'Publications',
        icon: mdiNewspaper,
        link: '/Publications'
      },
      {
        name: 'Presentation',
        icon: mdiPresentation,
        link: '/presentation'
      },
      {
        name: 'About',
        icon: mdiInformationVariant,
        link: '/about'
      }
    ]
  }),
  watch: {
    showNav: function(value) {
      this.show = !this.show;
    }
  }
};
</script>

<style scoped></style>
