<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
import Arweave from 'arweave'
import { Warp, WarpFactory } from 'warp-contracts'
import { onMounted, ref } from 'vue'

const arweave = Arweave.init({})
const warp = WarpFactory.forMainnet(undefined, undefined, arweave)
const cached = ref({})
onMounted(async () => {
  const contract = await warp.contract('kYoC3ShwsS8XSCyxM1_sLiMGmm-xrDBvxYEcx1-Dh1s');

  const { sortKey, cachedValue } = await contract.readState();
  cached.value = cachedValue

})





</script>

<template>
  Hello
  {{ cached }}
  
</template>
