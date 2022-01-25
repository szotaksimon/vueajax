<template>
    <div>
        <h1>Statue {{ $route.params.id }}</h1>    
        <table>
            <tr>
                <td>Person:</td>
                <td>{{ statue.person }}</td>
            </tr>
            <tr>
                <td>Height:</td>
                <td>{{ statue.height }}</td>
            </tr>
            <tr>
                <td>Price:</td>
                <td>{{ statue.price }}</td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
  data() {
    return {
      statue: {
        id: null,
        person: '',
        height: '',
        price: ''
      },
    }
  },
  methods: {
    async loadData() {
      const id = this.$route.params.id
      let Response = await fetch(`http://127.0.0.1:8000/api/statues/${id}`)
      let data = await Response.json()
      this.statue = {...data};
    },
  },
  mounted() {
      this.loadData()
  }
}
</script>

<style>

</style>