<script>
import { defineComponent } from 'vue';
import { NaLayout, NaSider, NaMenu, NaSubmenu, NaMenuItem, NaHeader, NaContent, NaFooter } from 'naive-ui';

export default defineComponent({
  name: 'App',
  components: { NaLayout, NaSider, NaMenu, NaSubmenu, NaMenuItem, NaHeader, NaContent, NaFooter },
  data() {
    return {
      menu: {
        ventas: ['clientes', 'facturas', 'devoluciones', 'reportes'],
        inventarios: ['productos', 'compras', 'egresos'],
        seguridad: ['usuarios', 'mi clave']
      },
      defaultOpeneds: ['ventas'],
      defaultActive: 'clientes'
    }
  }
});
</script>

<template>
  <na-layout>
    <na-sider>
      <na-menu :default-openeds="defaultOpeneds" :default-active="defaultActive" theme="dark" width="200">
        <template v-for="(items, key) in menu">
          <na-submenu :name="key">
            <template #title>{{ key }}</template>
            <na-menu-item v-for="item in items" :name="item" :key="item">{{ item }}</na-menu-item>
          </na-submenu>
        </template>
      </na-menu>
    </na-sider>
    <na-layout>
      <na-header style="background-color: #ffffff; height: 60px;"></na-header>
      <na-content style="padding: 24px; height: 100%;">
        <!-- Aquí puedes agregar el contenido de tus páginas -->
        <router-view></router-view>
      </na-content>
      <na-footer style="text-align: center;">&copy; {{ new Date().getFullYear() }} Mi empresa</na-footer>
    </na-layout>
  </na-layout>
</template>

<style>
/* Agrega aquí tus estilos personalizados */
</style>
