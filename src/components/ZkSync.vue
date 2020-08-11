<template>
  <div>
    zkSync
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from '@vue/composition-api';
import useAlerts from 'src/utils/alerts';
import useWalletStore from 'src/store/wallet';

function useZkSync() {
  const { notifyUser, showError } = useAlerts();
  const { signer, userAddress } = useWalletStore();

  onMounted(async () => {
    console.log(123123123);
    const zksync = await import('zksync');
    console.log(zksync);
  });

  return {};
}

export default defineComponent({
  name: 'zkSync',

  setup() {
    return { ...useZkSync() };
  },
});
</script>
