<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="justify-between" >


      <!-- <div class="row flex-center q-gutter-md shadow-5"> -->
        <div class=" flex justify-center items-center q-gutter-sm">
      
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar.png">
           </q-avatar>
           <div>Rensys Engineering </div>
       </div>
       <div class="flex flex-center q-gutter-sm ">
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar.png">
           </q-avatar>
        <div class="text-center">
        <div>Alemu Tebkew</div>
        <div class="text-caption">Admin</div>
        </div>
         
      </div>
  <!-- </div> -->
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>Menus</q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
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
import { defineComponent, ref } from 'vue';
import EssentialLink from 'components/EssentialLink.vue';

const linksList = [
  {
    title: 'Dashbored',
    icon: 'dashboard',
    link: '/dashboard',
  },
  {
    title: 'Survey',
    icon: 'mood',
    link: '/surveys',
  },
  {
    title: 'Data Collectore',
    icon: 'person',
    link: '/encoder',
  },
  {
    title: 'Settings',
    icon: 'settings',
    link: 'https://forum.quasar.dev',
  },
  {
    title: 'Logout',
    icon: 'logout',
    link: '/logout',
  },

];

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
