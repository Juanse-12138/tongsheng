<template>
    <div class="product-page">
      <div class="left-panel">
        <div class="category-title">
            <p>产品列表</p>
        </div>
        <div class="menu">
          <ul>
            <li v-for="product in products" :key="product.id" @click="selectProduct(product)">
              {{ product.name }}
            </li>
          </ul>
        </div>
      </div>
      <div class="right-panel">
        <div v-if="selectedProduct" class="product-overview">
          <img :src="selectedProduct.image" :alt="selectedProduct.name">
          <p>{{ selectedProduct.description }}</p>
        </div>
        <div v-else>
          <ul>
            <li v-for="product in products" :key="product.id">
              {{ product.name }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </template>
  
  <script>

import pic1 from "../../assets/images/product1.jpg"
import pic2 from "../../assets/images/product2.jpg"

  export default {
    data() {
      return {
        products: [
          {
            id: 1,
            category: '毫米波雷达设备',
            name: '毫米波雷达设备',
            image: pic1,
            description: '通过雷达干涉测量原理，实现对检测/监测目标位移的动态测量，最高采样率50Hz，采样精度优于0.1mm（30m米范围内）。应用场景：可广泛应用于中小跨径桥梁动位移监测、桥梁动静载试验、隧道收敛监测、和应急救援微小位移等监测/检测场景。',
            specification: '13 x 20 x 5 cm'
          },
          {
            id: 2,
            category: '通用智能网关',
            name: '通用智能网关',
            image: pic2,
            description: '通用智能网关集成路由+智能网关等功能，融合多种通信技术，北向支持通过RS485、4G/5G、WAN通信，快速接入物联网平台；南向支持RJ45、RS485、蓝牙、LORA、DEPLUS自组网通讯等通信方式，实现各类传感器的快速接入，获取设备状态及监测等数据。应用场景：建筑结构物、桥梁隧道、边坡等城市基础设施监测。',
            specification: '15 x 17 x 4 cm'
          },
          // 其他分类...
        ],
        selectedProduct: null,
      };
    },
    methods: {
      selectProduct(product) {
        this.selectedProduct = product;
      }
    }
  };
  </script>
  
  <style scoped>
  .product-page {
    display: flex;
  }
  
  .left-panel {
    flex: 1;
    justify-content: center; 
    text-align: center;
    align-items: center;
  }
  
  .menu {
    max-width: 180px;
    margin: 10px auto;
    text-align: center;
  }
  
  .menu ul {
    list-style: none;
    padding: 0;
  }
  
  .menu li {
    position: relative;
    border: 1px solid #bcbcbc;
    margin-bottom: 3px;
    display: block;
    font-size: 16px;
    line-height: 22px;
    color: #343434;
    padding: 10px 18px;
    background: #dcdcdc;
    cursor: pointer;
  }
  
  .right-panel {
    flex: 2;
    margin-top: 20px;
  }
  
  .right-panel img {
    max-width: 100%;
    height: auto;
  }

  .category-title {
    max-width: 180px;
    color:white;
    background: #3471b0;
    position: relative;
    margin: 10px auto;
    padding: 1px 0px;
    text-align: center;
}
.product-overview {
  display: inline-block;
    vertical-align: bottom;
    width: 30.333%;
    margin: 0 1.5% 20px 1.5%;
    padding: 10px;
    border: 1px solid #cccccc;
    -webkit-transition: all .5s ease;
    transition: all .5s ease;
}
  </style>
  