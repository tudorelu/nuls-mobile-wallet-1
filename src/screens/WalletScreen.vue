<template>
  <view class="container">


    <view class="details-container">
      <text class="small-text"> Total Balance </text>
      <text class="normal-text" v-if="balanceFiat!==undefined">$ {{balanceFiat}}</text>
      <text class="tiny-text" v-if="change!=undefined">{{change}}</text>
    </view>

    <view class="wallets-container">
      <text class="header-text"> Wallets </text>

      <flat-list
        :data="wallets"
       >
        <view 
          render-prop-fn="renderItem" 
          :style="{ 
            flex:1,
            flexDirection: 'row',
            justifyContent: 'space-between', 
            paddingVertical: 10,
            paddingHorizontal: 12,
            borderTopWidth: 1,
            borderColor: '#CED0CE'}">
          
          <text>{{args.item.key}}</text>
          <text>{{args.item.balance}}</text>
        </view>

      </flat-list>

      <fab
        :active="active"
        direction="up"
        :style="{ backgroundColor: '#ddd' }"
        position="bottomRight"
        :onPress="() => active=!active">
        <icon type="Feather" name="plus" />
        <button :style="{ backgroundColor: '#ddd' }">
          <icon type="MaterialCommunityIcons" name="arrow-down-bold-box-outline" />
        </button>
        <button :style="{ backgroundColor: '#ddd' }">
          <icon type="MaterialCommunityIcons" name="plus-box" />
        </button>

      </fab>

    </view>
    <!-- <view class="send-container">
      <text class="header"> Send NULS </text>

      <text class="input-label"> To Address </text>
      <text-input
        class="text-input"
        v-model="sendAddress"
      />

      <text class="input-label"> Amount </text>
      <text-input
        class="text-input"
        v-model="sendAmount"
      />

      <button
        color="#841584"
        :disabled="!isValidSendAddress()"
        :on-press="onSendPressed"
        title="Send NULS"
        accessibility-label="Send NULS"
      />
    </view> -->
  </view>
</template>
 
<script>

import '../../shim.js';
import * as NULS from 'nuls-js';
import Vue from 'vue-native-core'

import { Icon, Fab } from 'native-base';

Vue.component('icon', Icon);
Vue.component('fab', Fab);
export default {
  data: function() {
    return {
      wallet: this.navigation.getParam('wallet'),
      wallets:[
      {
        key:"niu3h78fh837fnuf837rfh",
        balance: 300756.12        
      }, {
        key:"hf87g8irwh783gf37rgf98",
        balance: 30523.1        
      }, {
        key:"euh9938y8yf387276g87g2",
        balance: 545.2        
      }],
      sendAddress: '',
      sendAmount: '',
      balanceFiat:30000.2,
      change:'+1.3%',
      active:false
    }
  },
  props: {
    navigation: {
      type: Object
    }
  },
  methods: {
    isValidSendAddress(){
      return NULS.isValidAddress(this.sendAddress);
    },
    onSendPressed(){
      console.log("Send Pressed!");
    }
  }
};
</script>

<style>
.container {
  background-color: white;
  align-items: center;
  flex: 1;
}

.details-container {
  flex: 1;  
  width:100%;
  background-color: #444;
  align-items: center;
  justify-content: center;
}

.wallets-container {
  flex: 2;  
  width:100%;
  background-color: #999;
}

.send-container {
  flex: 2;
  width:100%;
  background-color: #f0f0;
}

.text-color-primary {
  color: blue;
}

.text-input {
  height: 40px; 
  width: 90%;
  margin: 3px;
  margin-bottom: 10px;
  border-width: 1;
  border-color: gray;
  align-self:center;
}

.input-label {
  font-size: 20;
}

.header-text {
  font-size: 24;
  color: white;
  margin: 10px;
}

.normal-text {
  font-size: 24;
  color: white;
  margin-bottom: 5px;
}

.small-text {
  font-size: 15;
  color: white;
  margin-bottom: 3px;
}

.tiny-text {
  font-size: 13;
  color: white;
  margin-bottom: 1px;
}

.action-button-icon {
  font-size: 20;
  height: 22;
  color: pink;
}

</style>
