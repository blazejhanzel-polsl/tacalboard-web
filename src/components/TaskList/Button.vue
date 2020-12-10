<template>
  <button v-if="disabled" class="disabled">
    <span class="material-icons-outlined">{{ img }}</span>
    {{ text }}
  </button>
  <button v-else>
    <span class="material-icons-outlined">{{ img }}</span>
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    disabled: Boolean,
    img: String,
    text: String,
  },
};
</script>

<style lang="scss">
button {
  align-items: center;
  border: none;
  display: flex;
  font-family: sans-serif;
  font-size: 15px;
  height: 34px;
  justify-content: left;
  width: 100%;
}

button:hover {
  background-color: #f5f5f5 !important;
}

.disabled {
  background-color: transparent !important;
  color: #aaaaaa;
}

span {
  height: 24px;
  margin: 0px 5px 0px 5px;
  width: 24px;
}
</style>
