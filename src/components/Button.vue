<template>
  <button :disabled="isDisabled" :class="{'register-btn-disabled': isDisabled, 'register-btn': !isDisabled}">{{ text }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: [
    'text', 'isDisabled'
  ],
}
</script>

<style scoped>
  .register-btn {
    background: #0880AE;
    box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.08), 0px 4px 8px rgba(44, 39, 56, 0.08);
    border-radius: 6px;
    color: #fff;
    padding-top: 16px;
    padding-bottom: 16px;
    border: 2px solid #0880AE;
    outline: none;
    font-weight: 500;
  }
  .register-btn:hover {
    box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.08), 0px 24px 48px rgba(44, 39, 56, 0.16);
  }
  .register-btn:active {
    box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.0001), 0px 4px 8px rgba(44, 39, 56, 0.08);
    border: 2px solid rgba(44, 39, 56, 0.86);
  }
  .register-btn-disabled {
    background: #DBE2EA;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.08);
    border: none;
    color: #B1B5BF;
    border-radius: 6px;
    padding-top: 17px;
    padding-bottom: 17px;
    outline: none;
    font-weight: 500;
  }
</style>