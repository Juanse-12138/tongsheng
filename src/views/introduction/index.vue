<template>
    <div class="container">
      <div class="nav-buttons">
        <button v-for="(navItem, index) in navigationItems" :key="index" 
        @click="toggleNavigation(navItem)" 
        :class="{ 'nav-button': true, 'selected': navItem.name === currentNavigation.name }">
        {{ navItem.title }}</button>
      </div>
      <div class="content">
      <div v-if="currentNavigation">{{ currentNavigation.content }}</div>
    </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        currentNavigation: { title: '企业简介', content: 'Home Content', name: 'intro' },
        navigationItems: [
          { title: '企业简介', content: 'company introduction', name: 'intro' },
          { title: '企业文化', content: 'company culture', name: 'culture'},
          { title: '发展历程', content: 'development', name: 'development'},
          { title: '资质荣誉', content: 'honor & certificate', name: 'honor'},
          { title: '组织架构', content: 'organization', name: 'organization'}
        ]
      };
    },
    methods: {
      toggleNavigation(navItem) {
        this.currentNavigation = navItem;
      }
    }
  };
  </script>

<style scoped>
/* Add your CSS styles here */
.container {
    margin-top: 100px;
    text-align: center;
}
.nav-buttons {
    display: flex;
    flex-wrap: wrap;
    max-width: 600px; /* 设置最大宽度 */
    margin: 0 auto;
    margin-bottom: 20px;
}

.nav-button {
    flex: 1;
    border: 1px solid #dedede;
    text-align: center;
    width: 120px; /* 统一宽度 */
    height: 50px;
    font-size: small;
    float: left;
    background: #fff;
    border-bottom: 4px solid #dedede;
}
.nav-button:hover {
    color:#fff;
    background-color: rgb(52, 113, 176);
}
.content {
    padding: 20px;
    border: 1px solid #ccc;
}
.selected {
    color:#fff;
    background: #3471b0;
    background-image: initial;
    background-position-x: initial;
    background-position-y: initial;
    background-size: initial;
    background-repeat: initial;
    background-attachment: initial;
    background-origin: initial;
    background-clip: initial;
    background-color: rgb(52, 113, 176);
}
</style>