<template>
    <app-navigation></app-navigation>
</template>

<script>
import { StackNavigator } from "vue-native-router";
import FirstScreen from "./src/screens/FirstScreen.vue";
import WalletScreen from "./src/screens/WalletScreen.vue";
import PrivateKeyScreen from "./src/screens/PrivateKeyScreen.vue";

const AppNavigation = StackNavigator(
  {
    Home: {screen: FirstScreen},
    Wallet: {screen: WalletScreen},
    PrivateKey: {screen: PrivateKeyScreen},
  },
  {
    initialRouteName: 'Wallet',
  }
);
export default {
    components: { AppNavigation }
}
</script>