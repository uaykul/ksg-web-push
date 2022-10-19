<template>
  <div>
    <header> Web Push </header>
    <div class="app">
      <div class="categories">
        <category-item
          :category="category"
          v-for="category in categoryList"
          :key="category.id"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CategoryItem from "@/components/CategoryItem";
import axios from "axios";
export default {
  components: {
    CategoryItem,
  },
  data() {
    return {
      categoryList: [],
    };
  },
  created() {
    axios
      .get("https://damp-dawn-54546.herokuapp.com/")
      .then((categoryList_response) => {
        console.log("categoryList :>> ", categoryList_response);
        this.categoryList = categoryList_response.data.categoryList;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
