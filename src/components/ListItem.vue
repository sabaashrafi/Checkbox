<template>
  <b-list-group-item class="d-flex justify-content-around align-items-center">
    <b-icon :icon="listInfo.icon" :style="{ color: getRandomColor() }"></b-icon>
    {{ listInfo.name }}
    <b-form-input style="width:100px" value="23" type="number"></b-form-input
  ></b-list-group-item>
</template>

<script>
// This is a description of the component
export default {
  name: "ListItem",
  //list information in a object
  props: {
    listInfo: Object,
  },
  methods: {
    // @vuese
    //for choose a random color
    getRandomColor() {
      var letters = "0123456789ABCDEF";
      var color = "#";
      for (var i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    },
  },
};
</script>

