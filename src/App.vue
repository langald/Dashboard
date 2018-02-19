<template>
      <v-app>
        <v-content>
          <v-container class="mainWrap">
            <v-layout row wrap borderedBlock pad20>
              <v-flex lg1 md6 sm2 order-xs1 text-xs-left>
                <div class="logo">
                  <img src="./assets/logo-light.png" />
                  <img src="./assets/logo-dark.png" />
                </div>
              </v-flex>
              <v-flex lg7 md12 order-xs3 text-lg-left text-xs-center>
                <ul class="menuButtonBlock">
                  <menu-button
                    v-for="title in menuButtonTitle"
                    :key="title.name"
                    :title="title">
                  </menu-button>
                </ul>
              </v-flex>
              <v-flex lg4 md6  order-xs2 order-lg3 text-xs-right logoInfo>
                <div class="avatar"><div class="avatar__name">JA</div></div>
                <div class="user">
                  Javier Abadia
                  <i class="material-icons">keyboard_arrow_down</i>
                </div>
              </v-flex>
            </v-layout >

            <v-layout row wrap borderedBlock-left borderedBlock-right>
              <v-flex sm2 md1 hidden-xs-only text-xs-center leftPanel borderedBlock-bottom borderedBlock-right>
                <left-panel-item
                  v-for="(leftMenuItem, index) in leftMenuItems"
                  :key="index"
                  :leftMenuItem="leftMenuItem">
                </left-panel-item>
              </v-flex>

              <v-flex xs12 sm10 md11 text-xs-left dashboard>
               <v-layout row wrap headerBlock pad20 borderedBlock-bottom>
                  <v-flex md9 xs12 >
                    <dashboard-title :mainTitle="'Jeans'" :subTitle="'Top 5 retailers in USA'" ></dashboard-title>
                  </v-flex>
                  <v-flex md3 xs12 text-xs-right>
                    <search></search>
                  </v-flex>
               </v-layout>
               <v-layout row wrap>
                  <v-flex md8  xs12 borderedBlock-bottom borderedBlock-right pad20 dashboardItem>
                    <dashboard-title :mainTitle="'Price Analysis'" :subTitle="'Current'" :subTitleDark="'Full'"></dashboard-title>
                    <column-chart :series = "initSeries"></column-chart>
                  </v-flex>
                  <v-flex md4  xs12 borderedBlock-bottom pad20 dashboardItem>
                    <dashboard-title :mainTitle="'Assortment'"></dashboard-title>
                    <div class="assortment-progress">
                      <v-progress-circular class="colored"
                          :size="200"
                          :width="15"
                          :rotate="-90"
                          :value="10"
                        >
                        <balloon :balloonData="{ value: '10%', title: 'JEANS' }"></balloon>
                      </v-progress-circular>
                      <ul class="progressLegend">
                        <li>Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere</li>
                      </ul>
                    </div>
                  </v-flex>
               </v-layout>

               <v-layout row wrap>
                  <v-flex md8  xs12  dashboardItem>
                    <div class="borderedBlock-bottom borderedBlock-right pad20">
                      <dashboard-title :mainTitle="'Market activity'" :subTitle="'Past 7 days'" ></dashboard-title>
                      <ul class="marketActivityItems">
                        <li>
                          <div class="image-container">
                            <img src="./assets/new-styles.png" />
                          </div>
                          <balloon :balloonData="{ value: '68', title: 'NEW STYLES' }"></balloon>
                        </li>
                        <li>
                          <div class="image-container">
                            <img src="./assets/discounted.png" />
                          </div>
                          <balloon :balloonData="{ value: '499', title: 'DISCOUNTED' }"></balloon>
                        </li>
                        <li>
                          <div class="image-container">
                            <img src="./assets/sold-out.png" />
                          </div>
                          <balloon :balloonData="{ value: '42', title: 'SOLD OUT' }"></balloon>
                        </li>
                      </ul>
                    </div>
                    <v-layout row wrap>
                      <v-flex md6  xs12 borderedBlock-bottom borderedBlock-right pad20 dashboardItem>
                        <dashboard-title :mainTitle="'Top colors'" ></dashboard-title>
                        <ul class="topColorItems">
                          <li>
                            <top-colors :topColorsData="{ bgColor: '#a05813', title: 'BROWN', value: '#555555'}" ></top-colors>
                          </li>
                          <li>
                            <top-colors :topColorsData="{ bgColor: '#0d59ad', title: 'BLUE', value: '#555555'}" ></top-colors>
                          </li>
                          <li>
                            <top-colors :topColorsData="{ bgColor: '#d1ab7e', title: 'CREAM', value: '#555555'}" ></top-colors>
                          </li>
                        </ul>
                      </v-flex>
                      <v-flex md6  xs12 borderedBlock-bottom borderedBlock-right pad20 dashboardItem>
                        <dashboard-title :mainTitle="'Top materials'" ></dashboard-title>
                        <ul class="topMaterials">
                          <li>
                            <balloon :balloonData="{ value: '10%', title: 'WOOL' }"></balloon>
                          </li>
                          <li>
                            <balloon :balloonData="{ value: '8%', title: 'SPANDEX' }"></balloon>
                          </li>
                          <li>
                            <balloon :balloonData="{ value: '12%', title: 'OTHER WOOL' }"></balloon>
                          </li>
                        </ul>
                      </v-flex>
                    </v-layout>
                  </v-flex>
                  <v-flex md4  xs12 borderedBlock-bottom pad20 dashboardItem>
                    <dashboard-title :mainTitle="'Discount Trends'"></dashboard-title>
                     <div class="assortment-progress">
                      <v-progress-circular class="colored"
                          :size="150"
                          :width="5"
                          :rotate="-90"
                          :value="42"
                        >
                        <balloon :balloonData="{ value: '42%', title: 'ON SALE' }"></balloon>
                      </v-progress-circular>
                      <ul class="discountTrendBaloons">
                        <li>
                          <balloon :balloonData="{ value: '5%', title: 'Discount', topTitle: 'MIN' }"></balloon>
                        </li>
                        <li>
                          <balloon :balloonData="{ value: '10%', title: 'Discount', topTitle: 'AVG' }"></balloon>
                        </li>
                        <li>
                          <balloon :balloonData="{ value: '20%', title: 'Discount', topTitle: 'MAX' }"></balloon>
                        </li>
                      </ul>
                    </div>
                  </v-flex>
               </v-layout>
              </v-flex>
            </v-layout>
          </v-container>
        </v-content>
      </v-app>
</template>

<script>
import MenuButton from '@/components/MenuButton'
import LeftPanelItem from '@/components/LeftPanelItem'
import Search from '@/components/Search'
import DashboardTitle from '@/components/DashboardTitle'
import ColumnChart from '@/components/ColumnChart'
import Balloon from '@/components/Balloon'
import TopColors from '@/components/TopColors'

export default {
  name: 'App',
  components: { MenuButton, LeftPanelItem, Search, DashboardTitle, ColumnChart, Balloon, TopColors },
  data () {
    return {
      menuButtonTitle: [
        {name:"Overview", isActive:true},
        {name:"Promotions", isActive:false},
        {name:"Trends", isActive:false},
        {name:"Promo codes", isActive:false}
      ],
      leftMenuItems: [
        {src: require('./assets/shorts.png'), bgColor:"#27e9b6"},
        {src: require('./assets/sneakers.png'), bgColor:"#a389b2"},
        {src: require('./assets/bag.png'), bgColor:"#36b2f5"},
        {src: "", bgColor:"#e1e1e1"}
      ]
    }
  },
  computed: {
    initSeries : function() {
      return [{              
              data: [500, 700, 1000, 1300, 1500, 1700, 1400, 900, 800, 700, 500, 400, 400, 200, 300, 300, 250, 250, 300, 250, 100, 50],
              showInLegend: false
          }];
    }
  }
}


</script>

<style>
#app {
  font-family: 'Roboto Light', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 18px;
  color: #58595b;
  background-color: #fff;
}
.mainWrap {
  max-width: 1170px;
}

.borderedBlock {
  border: 1px solid #e1e1e1;  
}
.borderedBlock-top {
  border-top: 1px solid #e1e1e1;  
}
.borderedBlock-right {
  border-right: 1px solid #e1e1e1;  
}
.borderedBlock-bottom {
  border-bottom: 1px solid #e1e1e1;  
}
.borderedBlock-left {
  border-left: 1px solid #e1e1e1;  
}
.pad20 {
  padding: 20px;
}

.logo {
  display: inline-block;
  height: 47px;  
  margin: 10px;
  cursor: pointer;
}

.menuButtonBlock {
  display: inline-block;
}

.avatar {
  position: relative;
  display: inline-block;
  border-radius: 50%;
  width: 47px;
  height: 47px;
  background-color: #e1e1e1;
  color: #fff;
  margin: 10px;
}
.avatar__name {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.logoInfo {
  color: #939598;
  cursor: pointer;
}
.user {
  position: relative;
  display: inline-block;
  padding-right: 10px;
  margin-right: 30px;
}
.user i {
  position: absolute;
  top: 0;
}




.headerBlock {
  background-color: #f7f7f7;
}


.dashboardItem .dashboard__subtitle {
  cursor: pointer;
}

.assortment-progress {
  margin: 25px auto 0;
  text-align: center;
}
.colored {
  color: #27e9b6!important;
}


.progressLegend {
  font-size: 14px;  
  list-style-type: none;
  color: #58595b;
  text-align: left;
  margin-top: 20px;
}
.progressLegend li {
  position: relative;
  margin-left: 30px;
}
.progressLegend li:before {    
  position: absolute;
  top: 5px;
  left: -30px;
  background-color: #27e9b6;
  content: "";
  width: 10px;
  height: 10px;
  border-radius: 50%; 
}

.discountTrendBaloons li, .marketActivityItems li, .topColorItems li, .topMaterials li {
  list-style-type: none;  
  display: inline-block;
  margin: 20px 15px;  
}

.image-container {
  display: inline-block;
  width: 30%;
  max-width: 60px;
  height: auto;
  margin: 0 auto;
  overflow: hidden;
}
.image-container img {
  display: block; 
  max-width: 100%;
  height: auto;
  margin: 0 auto; 
}

.marketActivityItems, .topColorItems, .topMaterials {
  text-align: center;
}
.marketActivityItems li {
  vertical-align: baseline;
}
.marketActivityItems .balloon {
  text-align: left;
  margin-left: 15px;
}

.topMaterials li {
  margin: 20px 10px;
  text-align: left;
}
</style>
