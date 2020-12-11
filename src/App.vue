<template>
  <div id="app">
    <!-- top checkbox row -->
    <b-row>
      <b-col cols="4" v-for="(item, $index) in checkboxs" :key="$index">
        <b-form-checkbox
          v-model="checkboxs[$index].state"
          :value="checkboxs[$index].value"
          @change="changeOnCheckbox(checkboxs[$index])"
          name="check-button"
        >
          <b-icon :icon="item.icon"></b-icon> </b-form-checkbox
      ></b-col>
    </b-row>
    <!-- end checkbox row -->
    <hr />
    <!-- list items of checkbox selected -->
    <b-list-group>
      <!-- list item component -->
      <list-item
        v-for="(item, index) in ListItems"
        :key="index"
        :listInfo="item"
      ></list-item>
    </b-list-group>
    <!-- end list items -->
  </div>
</template>

<script>
import ListItem from "./components/ListItem";
// Task for showing each component selected
export default {
  name: "App",
  data() {
    return {
      checkboxs: [
        {
          icon: "folder-plus",
          value: "1",
          state: false,
          name: "bounding box",
          count: "3",
        },
        {
          icon: "person-fill",
          value: "2",
          state: false,
          name: "person",
          count: "4",
        },
        {
          icon: "grid3x3-gap",
          value: "3",
          state: false,
          name: "box corner",
          count: "2",
        },
      ],
      ListItems: [],
    };
  },
  components: { ListItem },
  methods: {
    // @vuese
    //fire when checkbox changes
    //@arg The argument is item of changed
    changeOnCheckbox(checkedItem) {
      if (checkedItem.state) {
        for (let i = 0; i <= checkedItem.count; i++) {
          this.ListItems.push(checkedItem);
        }
      } else {
        this.ListItems = this.ListItems.filter(function(checked) {
          return checked.value !== checkedItem.value;
        });
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
}
body {
  background-color: #2c3e50 !important;
}
hr {
  border-top: 1px solid rgba(255, 255, 255, 0.4);
}
.list-group-item {
  background-color: #2c3e50 !important;
}
.form-control{
    background-color: #2c3e50 !important;
    color: white !important;
}
</style>
