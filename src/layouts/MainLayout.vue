<template>
  <q-layout view="hHh lpR fFf">

    <q-header class="bg-black text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-img :src="'src/assets/club_milano_logo.jpg'"
                 style="height: 32px; max-width: 32px;" />
          <span class="text-light-green-14">C</span><span class="text-yellow-14">LUB</span> <span
                class="text-blue-14">ሚ</span><span class="text-red-14">ላኖ</span>
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer bordered
              class="bg-dark text-white">
      <q-toolbar>
        <q-toolbar-title>
          <div class="text-center text-weight-thin text-subtitle1 text-yellow-14">&copy;Club Milano 2024</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>
