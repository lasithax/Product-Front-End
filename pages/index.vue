<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-12 text-center">
        <h1 class="page-title">Product List</h1>
      </div>
    </div>

    <div class="search">
      <form class="input-group">
        <input type="search" class="form-control rounded" placeholder="Search" aria-label="Search"
          aria-describedby="search-addon" />
        <button type="button" class="btn btn-outline-primary">search</button>
      </form>
    </div>

    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Name</th>
          <th scope="col">Price</th>
          <th scope="col">Status</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products">
          <th scope="row">{{product.id}}</th>
          <td>{{product.name}}</td>
          <td>{{product.price}}</td>
          <td v-if="!product.status">Inactive</td>
          <td v-if="product.status">Active</td>
          <td class="action">
            <div class="actionBtn">
              <form method="" action="">
                <button type="button" class="btn btn-success"><i class="bi bi-check"/></button>
              </form>
            </div>
            <div class="actionBtn">
              <form method="" action="">
                <button type="button" class="btn btn-primary"><i class="bi bi-pencil-square"/></button>
              </form>
            </div>
            <div class="actionBtn">
              <form method="" action="">
                <button type="button" class="btn btn-dark"><i class="bi bi-arrow-right-short"/></button>
              </form>
            </div>
            <div class="actionBtn">
              <form method="" action="">
                <button type="button" class="btn btn-danger"><i class="fa fa-trash"/></button>
              </form>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'home',
  layout: 'dashboard',
  data() {
    return {
      products :[],
    }
  },
  methods: {
    getTasks(){
      this.$axios.get('api/products').then(response =>{
        this.products=response.data;
        console.log(this.task);
      })
    }
  },
  mounted(){
    this.getTasks();
  }
}
</script>

<style lang="css" scoped>
  .page-title {
    padding: 50px;
  }

  .input-group {
    padding-bottom: 40px;
    align-items: center;
    width: 60%;
  }

  .search {
    display: flex;
    justify-content: center;
  }
  .action{
    display: flex;
  }

.actionBtn{
    display: flex;
    padding: 10px;
  }

</style>
