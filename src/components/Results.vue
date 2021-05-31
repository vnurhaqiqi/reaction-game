<template>
  <h3>Reaction Time - {{ score }}/ms</h3>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "You born to be the Flash!";
    } else if (this.score < 400) {
      this.rank = "Faster than the Cannon Ball!";
    } else {
      this.rank = "The Normal One..";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>