<template>
  <div class="dropdown-wrapper">
    <span class="dropdown-title">{{ title }}</span>
    <div @mouseleave="isTouched = true" @click="dropdownVisible = !dropdownVisible" class="dropdown-block" :class="{'dropdown-block-open': dropdownVisible}" v-click-outside="close">
      <span class="dropdown-value">{{ value || title }}</span>
      <svg width="16" height="9" viewBox="0 0 16 9" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M8 6.58579L14.2929 0.292893C14.6834 -0.0976311 15.3166 -0.0976311 15.7071 0.292893C16.0976 0.683418 16.0976 1.31658 15.7071 1.70711L8.70711 8.70711C8.31658 9.09763 7.68342 9.09763 7.29289 8.70711L0.292893 1.70711C-0.0976311 1.31658 -0.0976311 0.683418 0.292893 0.292893C0.683418 -0.0976311 1.31658 -0.0976311 1.70711 0.292893L8 6.58579Z" fill="#0880AE"/>
      </svg>
    </div>
    <ul v-show="dropdownVisible" class="dropdown">
      <li class="dropdown-item" v-for="(item , ind) in items"
        @click="chooseItem(ind)" :key="item">
        {{ item }}
      </li>
    </ul>
    <span v-if="error && isTouched" class="dropdown-error">Введено не корректное значение</span>
  </div>
</template>

<script>
export default {
  name: 'Dropdown',
  props: [
    'value', 'title', 'items', 'error'
  ],
  data () {
    return {
      dropdownVisible: false,
      isTouched: false
    }
  },
  methods: {
    close () {
      this.dropdownVisible = false
    },
    chooseItem (ind) {
      this.$emit('input', this.items[ind])
      this.close()
    }
  }
}
</script>

<style scoped>
.dropdown-wrapper {
  position: relative;
}
.dropdown-title {
  font-weight: 500;
  color: #756F86;
}
.dropdown-block {
  border: 1px solid #DBE2EA;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
  border-radius: 6px;
  outline: none;
  padding: 16px 16px 14px 15px;
  margin-top: 7px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  user-select: none;
}
.dropdown-block-open {
  border: 2px solid #0880AE; 
  padding: 14px;
  padding-left: 15px;
}
.dropdown-value {
  color: #7C9CBF;
}
.dropdown {
  position: absolute;
  top: 85px;
  left: 0;
  border: 1px solid #DBE2EA;
  box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04), 0px 20px 20px rgba(44, 39, 56, 0.04);
  border-radius: 6px;
  background: #fff;
  width: 100%;
  padding: 12px 0;
  z-index: 10;
}
.dropdown-item {
  color: #756F86;
  padding: 12px 16px;
}
.dropdown-item:hover {
  background: #EBF4F8;
}
.dropdown-error {
  position: absolute;
  top: 85px;
  left: 0;
  font-size: 14px;
  line-height: 18px;
  color: #FF7171;
}
</style>