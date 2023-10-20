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
    console.error(e)
  }
}

</script>

<template>
  <button @click="fetchParams">Click</button>
  <div>Data: {{ status.data }}</div>
  <div>E: {{ status.e }}</div>
  <div>Source code: <a href="https://github.com/scholtz/vue-illegal-invocation">https://github.com/scholtz/vue-illegal-invocation</a></div>
  <div>Demo: <a href="https://vue-illegal-invocation.vercel.app/">https://vue-illegal-invocation.vercel.app/</a></div>
  <div>Solution to the problem: <code>npm i algosdk@2.4.0</code></div>
</template>
