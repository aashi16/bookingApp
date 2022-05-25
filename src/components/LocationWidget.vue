<template>
  <div class="location-widget">
    <place-autocomplete-field
      v-model="pickedLocation"
      @input="$emit('input', pickedLocation)"
      v-on:autocomplete-select="onAutoCompleteSelect"
      :key="selectedValue"
      placeholder="Enter an an address, zipcode, or location"
      name="pickedLocation"
      api-key="AIzaSyBzIZkf4qaNWaFNKhbvNbLfQEhGRPtikm0"
    >
    </place-autocomplete-field>
    <span class="widget-error"></span>
  </div>
</template>

<script>
import Vue from "vue";
import VuePlaceAutocomplete from "vue-place-autocomplete";

Vue.use(VuePlaceAutocomplete);
export default {
  name: "LocationWidget",
  data() {
    return {
      pickedLocation: "",
      selectedValue: "",
    };
  },
  methods: {
    onAutoCompleteSelect(val) {
      this.selectedValue = val.description;
    },
  },
};
</script>
<style lang="scss">
@import "bootstrap/scss/bootstrap.scss";
</style>
<style scoped>
.location-widget {
  margin-bottom: 20px;
  text-align: left;
  width: 100%;
  background-color: #fff;
  font-size: 16px;
  outline: none;
  box-shadow: none;
  border: none;
  border-radius: 10px;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.widget-text {
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
.location-widget >>> .form-group.input-field {
  margin-bottom: 0px;
}
.location-widget >>> .form-group.input-field input {
  border: none;
  outline: none;
  padding: 12px;
  height: unset;
}
.widget-error {
  font-size: 12px;
}
</style>
