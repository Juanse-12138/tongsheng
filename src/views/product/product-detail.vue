<template>
    <div class="productw">
        <div class="product-header">
            <div class="product-image">
            <img :src="selectedProduct.image">
            </div>
        <div class="product-info">
            <h2>{{ selectedProduct.name }}</h2>
            <p>产品尺寸： {{ selectedProduct.specification }}</p>
            <div class="buttons">
            <button @click="consult">咨询</button>
            <button @click="downloadManual">下载说明书</button>
            </div>
        </div>
        </div>

        <div class="product-description">
            <div class="snippet" v-if="selectedProduct.description">
                <h3>功能特点</h3>
                <p>{{ selectedProduct.description }}</p>
            </div>
            <div class="snippet" v-if="selectedProduct.techHighlight">
            <h3>技术亮点</h3>
            <p>{{ selectedProduct.techHighlight }}</p>
            </div>
            <div class="snippet" v-if="selectedProduct.usageScenario">
            <h3>使用场景</h3>
            <p>{{ selectedProduct.usageScenario }}</p>
            </div>
            </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      selectedProduct: Object
    },
    methods: {
    consult() {
      // 处理咨询按钮点击事件
    },
    downloadManual() {
      // 处理下载说明书按钮点击事件
    }
  }
  };
  </script>
  
  <style>

.product-header {
  display: flex;
  align-items: center;
}

.product-image img {
    height: 200px;
    width: 350px;
}

.product-info {
    margin-left: 150px;
    margin-bottom: 50px;
}

.snippet {
    width: 700px;
    position: relative;
    margin-bottom: 3%;
    background-color: aliceblue;
    border-radius: 47px;
    padding: 0 40px;
    background: url(../../assets/images/xqtb1.png) no-repeat top center #f3f7fa;
    padding-bottom: 1.5%;
}

.snippet h3 {
    height: 60px;
    text-align: left;
    line-height: 60px;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    overflow: hidden;
    margin-bottom: 15px;
    color:#3471b0;
}
  </style>
  