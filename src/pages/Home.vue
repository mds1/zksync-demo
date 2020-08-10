<template>
  <q-page padding class="text-center">
    <connect-wallet v-if="!userAddress" />
    <zk-sync v-else />
  </q-page>
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api';
import ConnectWallet from 'components/ConnectWallet.vue';
import ZkSync from 'components/ZkSync.vue';
import useWalletStore from 'src/store/wallet';

export default defineComponent({
  name: 'PageHome',
  components: { ConnectWallet, ZkSync },
  setup() {
    const { userAddress } = useWalletStore();
    return { userAddress };
  },
});
</script>
