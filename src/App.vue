<template>
  <b-row style="margin: 8px">
    <b-tabs>
      <b-tab title="Problem 1">
        <b-card
          style="
            margin: 20px;
            text-align: center;
            background-color: blanchedalmond;
            border-radius: 4px;
          "
        >
          <div>
            <div
              v-for="(item, index) in nameList"
              :key="index"
              v-on:click="deletePerson(index)"
              class="nameList"
            >
              {{ item }}
            </div>
            <b-button
              class="list_button"
              style="border-radius: 4px; width: 200px"
              v-on:click="addPerson"
            >
              add new person
            </b-button>
          </div>
        </b-card>
      </b-tab>
      <b-tab title="Problem 2">
        <b-col style="margin: 8px; padding: 0px;">
          <div style="margin-bottom: 18px; width: 200px">
              <b-form-radio-group v-model="option" >
                <b-form-radio value="1">Text</b-form-radio>
                <b-form-radio value="2">Date</b-form-radio>
              </b-form-radio-group>
          </div>
          <div v-if="option == 1">
            <b-form-input placeholder="Search name" style="width: 200px;"></b-form-input>
            <div style="margin-bottom: 8px" />
          </div>
          <div v-if="option == 2">
            <div style="margin-bottom: 8px">
              <b-dropdown
                text="before"
                variant="outline-primary"
                style="width: 200px; text-align: left"
              >
                <b-dropdown-item key="1"> before </b-dropdown-item>
                <b-dropdown-item key="2"> after </b-dropdown-item>
              </b-dropdown>
            </div>
            <b-form-datepicker style="width:200px; margin-bottom: 8px"/>
          </div>
          <b-button variant="outline-primary" style="margin-right: 10px; width:95px">Reset</b-button>
          <span><b-button variant="primary" style="width:95px">Search</b-button></span>
        </b-col>
      </b-tab>
    </b-tabs>
  </b-row>
</template>

<script>
import Vue from "vue";
Vue.use(require("vue-faker"));
Vue.use(require("ant-design-vue"));

export default {
  data() {
    return {
      nameList: ["Elaine Chang", "Caesar Yu", "Grace Wang"],
      option: "1",
    };
  },
  methods: {
    addPerson() {
      this.nameList.push(this.$faker().name.findName());
      console.log(this.nameList);
    },
    deletePerson(index) {
      Vue.delete(this.nameList, index);
    },
    // changType() {
    //   console.log(this.option);
    // },
  },
};
</script>

<style scoped>
.nameList {
  background-color: rgba(255, 255, 255, 0.6);
  border-radius: 4px;
  width: 200px;
  color: #666;
  padding: 0.5rem;
  margin: 1rem 0;
  border-radius: 4px;
}

.list_button {
  cursor: pointer;
  background: rgb(86, 177, 212);
  color: rgb(240, 240, 240);
  border-radius: 4px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
}
</style>
