<template>
    <div class="container">
    <img class="banner" src="../../assets/images/talent.jpeg" alt="">
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
        currentNavigation: { title: '技术合作', content: 'technique cooperation', name: 'intro' },
        navigationItems: [
          { title: '技术合作', content: 'technique cooperation', name: 'intro' },
          { title: '在线留言', content: 'online message', name: 'culture'},
          { title: '诚聘英才', content: 'talent recruitment', name: 'development'}
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
    text-align: center;
}
.nav-buttons {
    display: flex;
    flex-wrap: wrap;
    max-width: 600px; /* 设置最大宽度 */
    margin: 0 auto;
    margin-bottom: 20px;
}

.banner {
    width: 100%;
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