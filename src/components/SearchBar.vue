<template>
  <div>
    <input type="text" @input="onInput" placeholder="Enter the name of the movie or a search term" />
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onInput() {
      this.$emit('termChange', event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 20px;
}
</style>
