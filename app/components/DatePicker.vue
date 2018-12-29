<template>
  <StackLayout>
    <TextField :text="txt" @tap="selectDate" @focus="selectDate" :editable="false"/>
  </StackLayout>
</template>

<script>
const ModalPicker = require("nativescript-modal-datetimepicker")
  .ModalDatetimepicker;

const picker = new ModalPicker();

export default {
  props: ["parentref", "next"],
  data() {
    return {
      txt: "",
      isActive: false
    };
  },
  methods: {
    selectDate() {
      if (!this.isActive) {
        this.isActive = true;
        picker
          .pickDate({
            title: "Select Your Birthday",
            theme: "light",
            maxDate: new Date()
          })
          .then(result => {
            this.txt =
              "Date is: " + result.day + "-" + result.month + "-" + result.year;

            if (this.parentref && this.next) {
                let element = this.parentref[this.next];
                if (element) {
                    element.nativeView.focus();
                }
            }
          })
          .catch(error => {
            console.log("Error: " + error);
          });
        setTimeout(() => (this.isActive = false), 0);
      }
    }
  }
};
</script>

<style scoped>
</style>
