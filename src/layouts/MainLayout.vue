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
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          MAMS
        </q-toolbar-title>
        <div class="py-2">
        <q-btn-dropdown
          push
          @click="onMainClick"
          padding="xs"
        >
          <template v-slot:label>
            <q-avatar rounded>
              <img src="https://cdn.quasar.dev/img/avatar.png">
            </q-avatar>
          </template>

          <q-list>
            <q-item clickable v-close-popup @click="onItemClick">
              <q-item-section avatar>
                <q-avatar icon="exit_to_app" color="primary" text-color="white" />
              </q-item-section>
              <q-item-section>
                  <q-item-label>
                    Logout
                  </q-item-label>
              </q-item-section>
              <q-item-section side>
                <q-icon name="info" color="amber" />
              </q-item-section>
            </q-item>

            <q-item clickable v-close-popup @click="onItemClick">
              <q-item-section avatar>
                <q-avatar icon="assignment" color="secondary" text-color="white" />
              </q-item-section>
              <q-item-section>
                <q-item-label>Vacation</q-item-label>
                <q-item-label caption>February 22, 2016</q-item-label>
              </q-item-section>
              <q-item-section side>
                <q-icon name="info" color="amber" />
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown>
  </div>

      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
          class="min-height-50 py-3 text-bold text-lg text-center"
        >
          Mini Apartment Management System
        </q-item-label>

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

<script setup lang="ts">
import { ref } from 'vue';
import EssentialLink, { EssentialLinkProps } from 'components/EssentialLink.vue';

const onMainClick = () => {
    // console.log('Clicked on main button')
}
const onItemClick  = () => {
    // console.log('Clicked on main button')
}
const essentialLinks: EssentialLinkProps[] = [
  {
    title: 'Test ',
    caption: 'Code something',
    icon: 'description',
    link: '/test'
  },
  {
    title: 'Buildings',
    caption: 'Manage buildings',
    icon: 'home',
    link: '/building'
  },
];

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
