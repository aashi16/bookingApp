<template>
  <div class="room-section">
    <StepperBtn
      v-model="roomData"
      v-for="(type, index) of stepperTypes"
      :key="type.counterText"
      :counterText="type.counterText"
      @incrementNumb="incrementNumb(index)"
      @decrementNumb="decrementNumb(index)"
      :min="calcMin(index)"
      :max="calcMax(index)"
      :numb="type.counterNumb"
    />
  </div>
</template>

<script>
import StepperBtn from "./StepperBtn.vue";
export default {
  name: "RoomWidget",
  components: {
    StepperBtn,
  },
  data() {
    return {
      roomData: {},
      stepperTypes: [
        { id: 0, counterText: "Adult", counterNumb: 1 },
        { id: 1, counterText: "Child", counterNumb: 0 },
        { id: 2, counterText: "Room", counterNumb: 1 },
      ],
    };
  },

  methods: {
    getData() {
      this.roomData["Adult"] = this.stepperTypes[0].counterNumb;
      this.roomData["Child"] = this.stepperTypes[1].counterNumb;
      this.roomData["Room"] = this.stepperTypes[2].counterNumb;
    },
    incrementNumb(ide) {
      this.stepperTypes[ide].counterNumb++;
      this.getData();
      this.$emit("roomData", this.roomData);
    },
    decrementNumb(ide) {
      this.stepperTypes[ide].counterNumb--;
      this.getData();
      this.$emit("roomData", this.roomData);
    },
    calcMin(ide) {
      if (ide === 1) return 0;
      let exceedVal =
        this.stepperTypes[2].counterNumb === this.stepperTypes[0].counterNumb;
      if (ide === 0 && exceedVal) {
        return this.stepperTypes[0].counterNumb;
      }
      return 1;
    },
    calcMax(ide) {
      let exceedVal =
        this.stepperTypes[2].counterNumb === this.stepperTypes[0].counterNumb;
      if (ide === 2 && exceedVal) {
        return this.stepperTypes[2].counterNumb;
      }
    },
  },
};
</script>

<style scoped>
.room-section {
  display: flex;
  width: 100%;
  margin-bottom: 20px;
  justify-content: space-between;
}
.room-section >>> .stepper {
  width: 30%;
}
</style>
