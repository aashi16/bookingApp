<template>
  <div class="stepper">
    <div class="stepper-text">{{ counterText }}</div>
    <div class="stpper-button">
      <span
        class="button-increment"
        :class="{ disable: numb === max }"
        @click="incrementNumber"
      ></span>
      {{ numb }}
      <span
        class="button-decrement"
        :class="{ disable: numb === min }"
        @click="decrementNumber"
      ></span>
    </div>
  </div>
</template>
<script>
export default {
  name: "StepperBtn",
  props: {
    counterText: String,
    numb: Number,
    min: Number,
    max: Number,
  },
  data() {
    return {};
  },
  methods: {
    incrementNumber() {
      this.$emit("incrementNumb");
    },
    decrementNumber() {
      this.$emit("decrementNumb");
    },
  },
};
</script>

<style>
.stepper-text {
  text-align: left;
  color: #fff;
  font-size: 16px;
  font-weight: 500;
  text-transform: capitalize;
  margin-bottom: 4px;
}
.stpper-button {
  padding: 12px;
  align-items: center;
  background-color: #fff;
  font-size: 16px;
  outline: none;
  box-shadow: none;
  border: none;
  display: flex;
  justify-content: space-around;
  font-weight: 500;
  border-radius: 4px;
  text-overflow: ellipsis;
  white-space: nowrap;
  text-transform: capitalize;
}
.button-increment,
.button-decrement {
  font-weight: 600;
  height: 14px;
  width: 14px;
  opacity: 0.7;
  cursor: pointer;
}
.button-increment {
  background: url("../assets/increment.png");
  background-size: contain;
}
.button-decrement {
  background: url("../assets/decrement.png");
  background-size: contain;
}
span.disable {
  opacity: 0.2;
  pointer-events: none;
}
</style>
