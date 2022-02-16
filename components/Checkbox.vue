<template>
<div class="checkbox">
  <div class="promoted-checkbox">
    <input id="tmp" type="checkbox" class="promoted-input-checkbox"/>
    <label for="tmp">
      <icon-check class="ico checkbox" />
    </label>
  </div>
</div>
</template>

<script>
import IconCheck from "~icons/feather/check";
export default {
  components:{
    IconCheck,
  }
}
</script>

<style lang="scss" scoped>
$brand: #7F56D9;
$grey-25: #7F56D9;
$grey-5: #fcfcfc;

/* HTML5 Boilerplate accessible hidden styles */
.promoted-input-checkbox {
  border: 0;
  clip: rect(0 0 0 0);
  height: 1px; margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}

.promoted-checkbox {
  input:checked + label > svg {
    // Firefox doesn't render svg's that is loading with the use tag if its been set to display: none and then toggled to display: block, so you have to use tricks like this to get it to render again:
    height: 24px;
    animation: draw-checkbox ease-in-out 0.2s forwards;
  }

  label:active::after {
    background-color: $grey-25;
  }

  label {
    color: $brand;
    line-height: 20px;
    cursor: pointer;
    position: relative;
    &:after {
      content: "";
      height: 20px;
      width: 20px;
      margin-right: 1rem;
      float: left;
      border: 1px solid $brand;
      border-radius: 6px;
      transition: 0.15s all ease-out;
    }
  }
  svg {
    stroke: $brand;
    stroke-width: 5px;
    height: 0; //Firefox fix
    width: 11px;
    position: absolute;
    left: -36px;
    top: 1px;
    stroke-dasharray: 0; //Firefox fix
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
