<script>
export default {
  data() {
    return {
      API_HOST: "http://34.82.81.113:3000",
      students: [],
    };
  },
  mounted() {
    this.axios.get(`${this.API_HOST}/students`).then((response) => {
      this.students = response.data;
    });
  },
};
</script>

<template>
  <h1 class="text-3xl font-bold underline">Hello world!</h1>
  <table class="table">
    <thead>
      <tr>
        <th>ПІБ</th>
        <th>Наявність ПР</th>
        <th>Група</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in students">
        <td>
          <router-link v-bind:to="'/student-info/' + item._id">
            {{ item.name }}
          </router-link>
        </td>
        <td><input type="checkbox" v-model="item.isDonePr" /></td>
        <td>{{ item.group }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
table {
  @apply table-fixed text-xl bg-slate-400 border-black border-2 border-collapse m-10;
}
td, th{
  @apply border-black border-2 border-spacing-2 p-2;
}

</style>
