<template>
  <Page>
    <ActionBar title="Welcome to NativeScript-Vue!"/>
    <StackLayout>
      <TextField/>
      <DatePicker :parentref="$refs" next="testfield"/>
      <TextField ref="testfield"/>
      <DatePicker :parentref="$refs" next="secondfield"/>
      <TextField ref="secondfield" />
    </StackLayout>
  </Page>
</template>

<script>
import DatePicker from "./DatePicker";

export default {
  data() {
    return {
      msg: "Hello World!"
    };
  },
  methods: {},
  components: {
    DatePicker
  }
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}

.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}
</style>
