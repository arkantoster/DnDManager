<template>
  <q-layout view="hhh lpr fFf">

    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="fas fa-bars" @click="left = !left" />

        <q-toolbar-title>
          {{ name }}
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="left" side="left" bordered>
      <q-scroll-area class="fit">
          <q-list v-for="(menuItem, index) in menuList" :key="index">

            <q-item clickable :active="menuItem.label === 'Outbox'" v-ripple>
              <q-item-section avatar>
                <q-icon :name="menuItem.icon" />
              </q-item-section>
              <q-item-section>
                {{ menuItem.label }}
              </q-item-section>
            </q-item>

           <q-separator v-if="menuItem.separator" />

          </q-list>
        </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
export default {
  data () {
    return {
      left: false,
      name: 'D&D Manager',
      menuList: [
        {
          icon: 'fas fa-home',
          label: 'Home',
          separator: true
        },
        {
          icon: 'fas fa-user-alt',
          label: 'Players',
          separator: false
        },
        {
          icon: 'fas fa-user-friends',
          label: 'NPCs',
          separator: false
        },
        {
          icon: 'fas fa-dragon',
          label: 'Monsters',
          separator: true
        },
        {
          icon: 'fas fa-dice-d20',
          label: 'Initiative Tracker',
          separator: true
        }
      ]
    }
  }
}
</script>
