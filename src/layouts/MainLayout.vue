<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title> Mumec App </q-toolbar-title>

        <!-- <q-btn-dropdown icon="notifications" flat>
          <q-list>
            <q-item clickable v-close-popup @click="router.push({ name: 'profile' })">
              <q-item-section>
                <q-item-label>Perfil do usuário</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable v-close-popup @click="logout">
              <q-item-section>
                <q-item-label>Sair do Sistema</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown> -->
        <q-btn-dropdown icon="account_circle" flat>
          <q-list>
            <q-item clickable v-close-popup @click="router.push({ name: 'profile' })">
              <q-item-section>
                <q-item-label>Perfil do usuário</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable v-close-popup @click="logout">
              <q-item-section>
                <q-item-label>Sair do Sistema</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown>
      </q-toolbar>
    </q-header>

    <q-footer class="small-screen-only">
      <q-tabs>
        <q-route-tab exact replace icon="dashboard" label="Dashboard" :to="{ name: 'dashboard' }" />
        <q-route-tab exact replace icon="dvr" label="Ordem" :to="{ name: 'vender-modulo' }" />
        <q-route-tab exact replace icon="shelves" label="Estoque" :to="{ name: 'minhas-vendas' }" />
        <q-route-tab
          exact
          replace
          icon="schedule"
          label="Entregas"
          :to="{ name: 'minhas-vendas' }"
        />
      </q-tabs>
    </q-footer>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-img
        class="absolute-top"
        src="https://cdn.quasar.dev/img/material.png"
        style="height: 150px"
      >
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
          </q-avatar>
          <div class="text-weight-bold">Glêsio Santos</div>
          <div>Proprietário</div>
        </div>
      </q-img>
      <q-scroll-area
        style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd"
      >
        <q-list>
          <q-item-label header> Menu </q-item-label>

          <EssentialLink v-for="link in linksList" :key="link.title" v-bind="link" />
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Dashboard',
    caption: 'quasar.dev',
    icon: 'dashboard',
    link: 'https://quasar.dev',
  },
  {
    title: 'Produto',
    caption: 'Manutenção de produtos',
    icon: 'inventory_2',
    link: 'https://github.com/quasarframework',
  },
  {
    title: 'Fornecedores',
    caption: 'Manutenção de fornecedores do produtos',
    icon: 'contact_phone',
    link: 'https://github.com/quasarframework',
  },
  {
    title: 'Estoque',
    caption: 'Controle de produtos no estoque',
    icon: 'shelves',
    link: 'https://github.com/quasarframework',
  },
  {
    title: 'Serviços',
    caption: 'Manutenção de serviços da oficina',
    icon: 'inventory',
    link: 'https://chat.quasar.dev',
  },
  {
    title: 'Orçamento/Pedido',
    caption: 'Realizar pedidos ou orçamentos',
    icon: 'dvr',
    link: 'https://forum.quasar.dev',
  },
  {
    title: 'Clientes/Veiculos',
    caption: 'Registro de seus clientes e veculos',
    icon: 'groups',
    link: 'https://twitter.quasar.dev',
  },

  {
    title: 'Colaboradores',
    caption: 'Funcionários/Usuários do estabelecimentos',
    icon: 'supervisor_account',
    link: 'https://twitter.quasar.dev',
  },
  {
    title: 'Receita/Despesa',
    caption: 'Controle da sua movimentação',
    icon: 'bar_chart',
    link: 'https://facebook.quasar.dev',
  },
  {
    title: 'Agendamentos',
    caption: 'Controle de entrega de serviços',
    icon: 'schedule',
    link: 'https://twitter.quasar.dev',
  },
  {
    title: 'Estabelecimento',
    caption: 'Informações do seu estabelecimentos',
    icon: 'domain',
    link: 'https://facebook.quasar.dev',
  },
  {
    title: 'Assinatura/Planos',
    caption: 'Acompanhamento de sua assinatura',
    icon: 'payments',
    link: 'https://awesome.quasar.dev',
  },
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
