<template>
  <div id="app">
    <div class="container" style="text-align:center;">
      <div class="row">
        <div class="col-12">
          <div class="SerchSec">
            <h2>Search Form Using Vue.js</h2>
            <input
              type="text"
              placeholder="Search.."
              v-model="searchVal"
              ref="mainInput"
            />
            <div class="row" style="margin-top: 2rem;">
              <div
                class="col-lg-2 col-md-3 col-sm-4 col-6"
                v-for="(item, index) in comFontFunc"
                :key="index"
              >
                <div class="itemContent">
                  <i :class="'fa fa-' + item.item_name"></i>
                  <h4>{{ item.item_name }}</h4>
                  <p>{{ item.item_color }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import fontJson from "@/json/mainJson.json";
export default {
  mounted() {
    this.$refs.mainInput.focus();
  },
  data() {
    return {
      searchVal: "",
      items: fontJson
    };
  },
  computed: {
    comFontFunc() {
      return this.searchVal != ""
        ? this.items.filter(element => {
            return element.item_name.match(this.searchVal);
          })
        : this.items;
    }
  }
};
</script>
