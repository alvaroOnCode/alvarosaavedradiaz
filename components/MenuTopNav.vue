<template>
  <div class="header--menu-top-nav">
    <a-menu mode="horizontal">
      <a-sub-menu>
        <span slot="title" class="submenu-title-wrapper">
          <nuxt-link to="/blog">
            <a-icon type="setting" />Blog
          </nuxt-link>
        </span>

        <a-menu-item key="setting:1">JavaScript</a-menu-item>
        <a-menu-item key="setting:1">MongoDB</a-menu-item>
        <a-menu-item key="setting:1">NodeJS</a-menu-item>
        <a-menu-item key="setting:1">NuxtJS</a-menu-item>
        <a-menu-item key="setting:2">VueJS</a-menu-item>
      </a-sub-menu>
    </a-menu>
  </div>
</template>

<script>
export default {};
</script>