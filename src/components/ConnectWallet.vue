<template>
  <div>
    <div class="text-h6 q-mb-xl">
      Connect a wallet to get started
    </div>
    <q-btn color="primary" label="Connect wallet" @click="connectWallet" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api';
import { Dark } from 'quasar';
import useWalletStore from 'src/store/wallet';

import Web3Modal from 'web3modal';
import WalletConnectProvider from '@walletconnect/web3-provider';

function useWallet() {
  const { setProvider } = useWalletStore();

  async function connectWallet() {
    const providerOptions = {
      walletconnect: {
        package: WalletConnectProvider,
        options: {
          infuraId: process.env.INFURA_ID,
        },
      },
    };

    const web3Modal = new Web3Modal({
      network: 'mainnet',
      providerOptions,
      theme: Dark.isActive ? 'dark' : 'light',
    });

    await setProvider(await web3Modal.connect());
  }

  return { connectWallet };
}

export default defineComponent({
  name: 'ConnectWallet',

  setup() {
    return { ...useWallet() };
  },
});
</script>
