<template>
  <div class="date-widget">
    <div class="widget">
      <date-picker
        ref="datepicker"
        v-model="datePicked"
        placeholder="Please select the dates"
        range
        :popup-style="{ position: 'fixed' }"
        :disabled-date="disabledBeforeToday"
        @change="onChange"
      />
      <div ref="target"></div>
    </div>
  </div>
</template>

<script>
import DatePicker from "vue2-datepicker";
import "vue2-datepicker/index.css";
export default {
  name: "DateWidget",
  components: {
    DatePicker,
  },
  data() {
    return {
      datePicked: null,
    };
  },
  methods: {
    disabledBeforeToday(date) {
      const today = new Date();
      today.setHours(0, 0, 0, 0);
      return date < today;
    },
    onChange(val) {
      this.$emit("dateWidgetData", val);
    },
  },
  mounted() {
    const el = this.$refs.datepicker.$refs.popup.$el;
    this.$refs.target.appendChild(el);
  },
};
</script>

<style scoped>
.date-widget {
  width: 100%;
  margin-bottom: 20px;
}

.widget >>> .mx-datepicker {
  width: 100%;
}
.widget >>> input {
  cursor: pointer;
  text-align: left;
  width: 100%;
  padding: 12px;
  background-color: #fff;
  font-size: 16px;
  outline: none;
  box-shadow: none;
  border: none;
  border-radius: 4px;
  text-overflow: ellipsis;
  white-space: nowrap;
  height: unset;
  line-height: unset;
}
.widget >>> .mx-shortcuts-wrapper {
  display: none;
}
.widget >>> .mx-range-wrapper {
  max-width: 100vw;
}
.widget >>> .mx-calendar {
  float: none;
}
.widget >>> .mx-calendar-content {
  width: auto;
}
/* Mobile CSS */
@media screen and (max-width: 700px) {
  .widget >>> .mx-calendar {
    width: 100%;
  }
  .widget >>> .mx-datepicker-main {
    right: unset;
    left: 0 !important;
    top: unset !important;
    bottom: 0;
  }
}
</style>
