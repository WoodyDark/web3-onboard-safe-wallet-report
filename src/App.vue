<script setup lang="ts">
import Onboard from '@web3-onboard/core'
import injectedModule from '@web3-onboard/injected-wallets'
import safeModule from '@web3-onboard/gnosis'

const chains = [
  {
    id: 1,
    token: 'ETH',
    label: 'Ethereum Mainnet',
    rpcUrl: 'https://mainnet.infura.io/v3/${INFURA_ID}'
  },
  {
    id: 42161,
    token: 'ARB-ETH',
    label: 'Arbitrum One',
    rpcUrl: 'https://rpc.ankr.com/arbitrum'
  }
]

const onboard = Onboard({
  // This javascript object is unordered meaning props do not require a certain order
  wallets: [injectedModule(), safeModule()],
  chains,
  appMetadata: {
    name: 'Test Dapp',
    description:
      'Trade and hedge future yield with Pendle. Manage your yields based on your risk appetite, get fixed yield or lever up your yield exposure with no liquidation risk.'
  }
})
</script>

<template>
  <header>
    <div class="wrapper">
      <div>web3-onboard Safe wallet test</div>
      <nav>
        <button @click="onboard.connectWallet()">Connect Wallet</button>
      </nav>
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
