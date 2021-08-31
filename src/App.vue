<template>
  <h1>HelloJack!</h1>

  <table>
    <thead>
      <tr>
        <th>coin</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="coin in coins" :key="coin.id">
        {{
          coin.name
        }}
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      coins: [],
    };
  },

  async mounted() {
    const res = await fetch(
      'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false'
    );
    const data = await res.json();
    console.log(data);
    this.coins = data;
  },
};
</script>

<style></style>
