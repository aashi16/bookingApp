<template>
  <div class="layout">
    <div class="layout-top-section"></div>
    <div class="layout-search-section">
      <div class="alert alert-success" v-if="isSuccessful">
        <span @click="resetData">x</span>
        Your Booking is Confirmed. Enjoy your Stay!
      </div>
      <LocationWidget
        :class="{ error: placeError }"
        @input="placeData"
        v-model="locationInfo"
      />
      <RoomWidget @roomData="roomData" v-model="roomInfo" />
      <DateWidget
        :class="{ error: dateError }"
        @dateWidgetData="dateWidgetData"
        v-model="dateInfo"
      />
      <button @click="checkForHotel">Search</button>
    </div>
  </div>
</template>

<script>
import LocationWidget from "./LocationWidget.vue";
import RoomWidget from "./RoomWidget.vue";
import DateWidget from "./DateWidget.vue";
import axios from "axios";
export default {
  name: "WelcomePage",
  components: {
    LocationWidget,
    RoomWidget,
    DateWidget,
  },
  data() {
    return {
      locationInfo: "",
      roomInfo: "",
      dateInfo: "",
      placeError: false,
      dateError: false,
      isSuccessful: false,
    };
  },
  methods: {
    dateWidgetData(val) {
      this.dateError = false;
      this.dateInfo = val;
    },
    roomData(val) {
      this.roomInfo = val;
    },
    placeData(val) {
      this.placeError = false;
      this.locationInfo = val;
    },
    resetData() {
      this.isSuccessful = false;
      window.location.reload();
    },
    checkForHotel() {
      if (this.locationInfo !== "" && this.dateInfo !== "") {
        try {
          axios.post("http://localhost:3000/bookings", {
            location: this.locationInfo,
            accomodation: this.roomInfo,
            reservationDate: this.dateInfo,
          });
          this.isSuccessful = true;
        } catch (e) {
          console.error(e);
        }
      }
      if (this.locationInfo === "") {
        this.placeError = true;
      }
      if (this.dateInfo === "") {
        this.dateError = true;
      }
    },
  },
};
</script>

<style scoped>
.layout {
  height: 100vh;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}
.alert.alert-success {
  position: absolute;
  top: -70px;
  width: 110%;
}
.alert.alert-success span {
  position: absolute;
  top: -10px;
  right: -10px;
  background-color: #145724;
  border-radius: 50%;
  height: 20px;
  width: 20px;
  font-size: 14px;
  color: #d4edd9;
  display: flex;
  align-items: center;
  cursor: pointer;
  justify-content: center;
}
.layout-top-section {
  width: 100%;
  background: url("../assets/section-bg.jpeg");
  background-size: cover;
  overflow: hidden;
  background-position: center;
  height: 100%;
  position: relative;
  filter: brightness(0.4);
  object-fit: cover;
}
.layout-search-section {
  position: fixed;
  top: 150px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  width: 80%;
}
.layout-search-section .error {
  border: 2px solid #ff1e1e;
  border-radius: 4px;
}
.layout >>> .lx-toast.lx-toast-center {
  color: #155724;
  background-color: #d4edda;
  border-color: #c3e6cb;
}
button {
  width: 100%;
  padding: 15px 10px;
  background-color: #371111;
  color: #fff;
  font-size: 16px;
  outline: none;
  box-shadow: none;
  border: none;
  border-radius: 4px;
}
@media screen and (min-width: 700px) {
  .layout-search-section {
    width: 400px;
    margin-right: 5%;
  }
  .layout {
    justify-content: flex-end;
  }
}
</style>
