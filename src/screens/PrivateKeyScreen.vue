<template>
  <view class="container">

    <text> Private Key </text>
    <text-input
      :style="{height: 40, width: '90%', borderColor: 'gray', borderWidth: 1}"
      v-model="privateKey"
    />
    <button
        :disabled="!isValidPrivateKey()"
        :on-press="onImportPressed"
        title="Import Wallet"
        color="#841584"
        accessibility-label="Import an existing NULS wallet"
    />

  </view>
</template>
 
<script>
import '../../shim.js';
import * as NULS from 'nuls-js';

export default {
  data: function() {
    return {
      privateKey:null,
      wallet: null
    };
  },
  props: {
    navigation: {
      type: Object
    }
  },
  methods: {
    onImportPressed() {
      this.wallet = new NULS.Account().import(this.privateKey);
      this.navigation.navigate("Wallet", {wallet: this.wallet});
    },
    isValidPrivateKey(){
      return NULS.isValidPrivateKey(this.privateKey);
    }
  }
};
</script>

<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
</style>