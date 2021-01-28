<template>
  <div class="checkbox">
    <input type="checkbox" :checked="value">
    <span @click="onChange"></span>
  </div>
</template>

<script>
export default {
  name: 'Checkbox',
  props: [
    'value'
  ],
  methods: {
    onChange () {
      this.$emit('input', !this.value)
    }
  }
}
</script>

<style scoped>
.checkbox input {
  display: none;
}
.checkbox span {
  border: 1px solid #DBE2EA;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
  border-radius: 4px;
  width: 28px;
  height: 28px;
  margin: 0;
  outline: none;
  display: inline-block;
  position: relative;
  user-select: none;
}
.checkbox input:checked + span:before {
  content: url(../assets/img/check.svg);
  position: absolute;
  top: 0;
  left: 0;
  color:green;
  border: 2px solid #0880AE;
  border-radius: 4px;
  width: 28px;
  height: 28px;
  padding-left: 4px;
}

</style>