<template>
  <view class="container">

    <button title="Generate New Wallet" :onPress="() => onGenerateWallet()" />
    <button title="Import Existing Wallet" :onPress="() => onImportWallet()" />
    
  </view>
</template>
 
<script>
import '../../shim.js';
import { Account } from 'nuls-js';

export default {
  data: function() {
    return {
      wallet: {

      },
    };
  },
  props: {
    navigation: {
      type: Object
    }
  },
  methods: {
    onGenerateWallet() {
      this.navigation.navigate("Wallet", {wallet: new Account().create()});
    },
    onImportWallet() {
      this.navigation.navigate("PrivateKey", {message:"None is the message"});
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
