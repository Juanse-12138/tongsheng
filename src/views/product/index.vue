<template>
  <div>
    <img class="banner" src="../../assets/images/banner.jpg" alt="">
    <div class="product-page">
      <div class="left-panel">
        <div class="category-title">
            <p>产品列表</p>
        </div>
        <div class="menu">
          <ul>
            <li v-for="product in products" :key="product.id" @click="selectProduct(product)"
            :class="{ 'selected': selectedProduct.id === product.id }">
              {{ product.name }}
            </li>
          </ul>
        </div>
      </div>
      <div class="right-panel">
        <div v-if="selectedProduct">
          <product-detail :selectedProduct="selectedProduct"></product-detail>
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
  </div>
    
  </template>
  
  <script>

import pic1 from "../../assets/images/product1.jpg"
import pic2 from "../../assets/images/product2.jpg"
import pic3 from "../../assets/images/product3.png"
import productDetail from "./product-detail.vue";

  export default {
    components: {
        productDetail
      },
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
            specification: '15 x 17 x 4 cm',
            usageScenario: '建筑与基础设施结构安全监测。'
          },
          {
            id: 3,
            category: '多功能动态数据高速采集系统',
            name: '多功能动态数据高速采集系统',
            image: pic3,
            description: '多功能动态数据高速采集系统主要包含信号激励、信号采集和信号处理三大功能，配套上位机软件控制；可激励正弦波、雷克子波、余弦子波等常见超声信号，支持自定义调制信号的激励和超声编码信号源激励；设备具有8通道同步高速采集性能，每通道采样率80MHz，通道本地噪声小于1mv，采样千兆网口通讯方式，免驱动。',
            specification: '40 x 35 x 20 cm',
            techHighlight: '信号激励模块首次支持超声编码信号的激励，软硬件配合，使得超声无损感知系统“看得远、看得清',
            usageScenario: '结构损伤主动式超声无损检测、结构及材料被动叩诊法损伤检测、声发射被动式信号采集。'
          },
          // 其他分类...
        ],
        selectedProduct: {
            id: 1,
            category: '毫米波雷达设备',
            name: '毫米波雷达设备',
            image: pic1,
            description: '通过雷达干涉测量原理，实现对检测/监测目标位移的动态测量，最高采样率50Hz，采样精度优于0.1mm（30m米范围内）。应用场景：可广泛应用于中小跨径桥梁动位移监测、桥梁动静载试验、隧道收敛监测、和应急救援微小位移等监测/检测场景。',
            specification: '13 x 20 x 5 cm'
          },
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

.banner {
    width: 100%;
    height: 400px;
}
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
  .menu li:hover{
    color: white;
    background: #3471b0;
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

.selected {
  color: white;
  background: #3471b0;
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
  