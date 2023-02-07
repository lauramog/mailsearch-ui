<template>
  <div class="flex flex-col justify-center items-center">

    <h1>{{ msg }}</h1>
    <div class="container">
      <div class="card">
        <div class="card-body">
          <div class="input-group input-group-sm">
            <input type="text" ref="get_term" class="form-control ml-2" placeholder="Title" id="get-data" />
            <div class="input-group-append">
              <button @click="getData">search term</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="container">
      <h3 class="p-3 text-center"></h3>
      <table class="table-fixed ">
        <thead>
          <tr class="border">
            <th>subject</th>
            <th>From</th>
            <th>To</th>
            <th>Message</th>
          </tr>
        </thead>
        <tbody>
          <tr class="border" v-for="item in listItems">
            <td class="border"> {{ item.Subject }} </td>
            <td class="border">{{ item.From }}</td>
            <td class="border">{{ item.To }}</td>

            <p class="p" v-if="!readActivated">{{ item.Message.slice(0, 100) }}
            <div class="flex space-x-2 justify-center"></div>
            <button type="button" data-mdb-ripple="true" data-mdb-ripple-color="light"
              class="inline-block px-6 py-2.5  bg-teal-400 text-white font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-blue-700 hover:shadow-lg focus:bg-blue-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-blue-800 active:shadow-lg transition duration-150 ease-in-out"
              v-if="!readActivated" @click="activateReadMore">...Read all </button>
            </p>
            <p class="p" v-if="readActivated">{{ item.Message }}</p>
            <div class="flex space-x-2 justify-center"></div>

          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
const baseURL = "http://localhost:8081";
export default {
  name: 'InitialPage',
  props: {
    msg: String
  },
  data() {
    return {
      listItems: [],
      readActivated: false
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
    },
    activateReadMore() {
      this.readActivated = true;
    }
  },
  mounted() {
    this.getData()
  }
}
</script>