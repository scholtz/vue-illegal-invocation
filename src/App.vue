<script setup lang="ts">
import algosdk from 'algosdk';
import { reactive } from 'vue';

const status = reactive({
  data: {},
  e:{}
})
async function fetchParams(){
  try{
    const client = new algosdk.Algodv2('', 'https://mainnet-api.algonode.cloud', 443)
    const params = await client.getTransactionParams().do();
    status.data = params
  }catch(e:any){
    status.e = e;
  }
}

</script>

<template>
  <button @click="fetchParams">Click</button>
  <div>Data: {{ status.data }}</div>
  <div>E: {{ status.e }}</div>
</template>
