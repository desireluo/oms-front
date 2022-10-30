<template>
  <div class="list">


    <table>

      <thead>
      <tr>
        <th>name</th>
      </tr>
      </thead>

      <tbody>

      <tr v-for="item in list">
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.createdAt }}</td>
      </tr>
      </tbody>

    </table>


  </div>
</template>


<script>
import axios from "axios";

export default {

  data() {
    return {
      "list": []
    }
  }, created() {

    this.fetchData();

  },
  methods: {

    fetchData() {

      const data = axios.get("https://635e3b8003d2d4d47aea4a17.mockapi.io/api/v1/users").then(response => {

        this.list = response.data;
      });

    }
  }
}

</script>


<style>
@media (min-width: 1024px) {
  .list {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
