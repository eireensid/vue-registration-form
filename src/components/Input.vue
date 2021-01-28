<template>
  <div class="input-block">
    <label class="input-title" for="id">{{ title }}</label>
    <input @blur="isTouched = true" class="input" :id="id" :type="type" :placeholder="placeholder" @input="$emit('input', $event.target.value)">
    <span v-if="error && isTouched" class="input-error">Введено не корректное значение</span>
  </div>
</template>

<script>
export default {
  name: 'Input',
  props: [
    'id', 'type', 'title', 'placeholder', 'error'
  ],
  data () {
    return {
      isTouched: false
    }
  }
}
</script>

<style scoped>
.input-block {
  display: flex;
  flex-direction: column;
  position: relative;
}
.input-title {
  font-weight: 500;
  color: #756F86;
  padding-bottom: 7px;
}
.input {
  border: 1px solid #DBE2EA;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
  border-radius: 6px; 
  outline: none;
  padding: 15px;
  padding-right: 0;
}
.input::placeholder {
  color: #7C9CBF;
}
.input:focus {
  border: 2px solid #0880AE; 
  padding: 14px;
  padding-right: 0;
}
.input-error {
  position: absolute;
  top: 85px;
  left: 0;
  font-size: 14px;
  line-height: 18px;
  color: #FF7171;
}
</style>