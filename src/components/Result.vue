<template>
  <p>Reaction Time : {{ skorAKhir }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["skorAKhir"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.skorAKhir < 250) {
      this.rank = "Ninja Fingers";
    } else if (this.skorAKhir < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "snail pace";
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