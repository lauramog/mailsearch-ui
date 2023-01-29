<template>
  <h1>{{ msg }}</h1>
  <div class="container">
    <div class="card">
      <div class="card-header">GET data</div>
      <div class="card-body">
        <div class="input-group input-group-sm">
          <input type="text" ref="get_term" class="form-control ml-2" placeholder="Title" id="get-data" />
          <div class="input-group-append">
            <button class="btn btn-sm btn-primary" @click="getData">Get</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="container">
    <h3 class="p-3 text-center"></h3>
    <table class="table-auto">
      <thead>
        <tr>
          <th>subject</th>
          <th>From</th>
          <th>To</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in listItems">
          <td> {{ item.subject }} </td>
          <td>{{ item.From }}</td>
          <td>{{ item.to }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
const baseURL = "http://localhost:8081";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      listItems: []
    }
  },
  methods: {
    async getData() {
      const term = this.$refs.get_term.value;
      if (term !== "") {
        let url = `${baseURL}/search?term=${term}`;
        console.log("fetching data", url);
        const res = await fetch(url);
        const finalRes = await res.json();
        this.listItems = finalRes;
      }
    }
  },
  mounted() {
    this.getData()
  }

}
</script>
