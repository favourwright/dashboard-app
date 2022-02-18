<template>
<div :class="{'minus':!is_check_mark}">
  <svg v-if="is_check_mark" xmlns="http://www.w3.org/2000/svg" style="display: none">
    <symbol id="checkmark" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-miterlimit="10" fill="none"  d="M22.9 3.7l-15.2 16.6-6.6-7.1">
      </path>
    </symbol>
  </svg>
  <svg v-else width="14" height="14" style="display:none;" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path id="minus" d="M2.91669 7H11.0834" stroke="#7F56D9" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>

  <div class="checkbox">
    <input :id="name" type="checkbox" class="input-checkbox"/>
    <label :for="name">
      <svg><use :xlink:href="`#${is_check_mark?'checkmark':'minus'}`" /></svg>
    </label>
  </div>
</div>
</template>

<script>
import IconCheck from "~icons/feather/check";
export default {
  props:{
    name:{default:'temp',String},
    is_check_mark:{default:true,Boolean}
  },
  components:{
    IconCheck,
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/sass/resources';
/* HTML5 Boilerplate accessible hidden styles */
.input-checkbox {
  border: 0;
  clip: rect(0 0 0 0);
  height: 1px; margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}

.checkbox {
  input:checked + label > svg {
    // Firefox doesn't render svg's that is loading with the use tag if its been set to display: none and then toggled to display: block, so you have to use tricks like this to get it to render again:
    height: 24px;
    animation: draw-checkbox ease-in-out 0.2s forwards;
  }

  label:active::after {
    background-color: $primary;
  }

  label {
    color: $primary;
    line-height: 20px;
    cursor: pointer;
    position: relative;
    &:after {
      content: "";
      height: 20px;
      width: 20px;
      margin-right: 1rem;
      float: left;
      border: 1px solid $primary;
      background: $primary_faded;
      border-radius: 6px;
      transition: 0.15s all ease-out;
    }
  }
  svg {
    stroke: $primary;
    stroke-width: 5px;
    height: 0; //Firefox fix
    width: 11px;
    position: absolute;
    left: -32px;
    top: -2px;
    stroke-dasharray: 0; //Firefox fix
  }
}
.minus{
  svg{
    width: 12px;
    left: -34px;
    top: 4px;
  }
}

@keyframes draw-checkbox {
  0% {
    stroke-dashoffset: 0;
  }
  100% {
    stroke-dashoffset: 33;
  }
}
</style>
