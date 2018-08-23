<template>
  <section class="container">
    <div>
      <logo/>
      <h1 class="title">
        nuxt
      </h1>
      <h2 class="subtitle">
        My first-class Nuxt.js project
      </h2>
      <div class="links">
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">Documentation</a>
        <a href="https://github.com/nuxt/nuxt.js" target="_blank" class="button--grey">GitHub</a>
      </div>
      <el-table
      :data="sample.data"
      style="width: 100%">
      <el-table-column
        prop="account_id"
        label="account_id"
        width="180">
      </el-table-column>
      <el-table-column
        prop="exec_status"
        label="exec_status"
        width="180">
      </el-table-column>
      <el-table-column
        prop="order_type"
        label="order_type">
      </el-table-column>
    </el-table>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios';

export default {
  components: {
    Logo
  },
  data() {
    return {
      sample2: 'hogehoge'
    }
  },
  async asyncData({ app, params }) {
    const { data } = await axios.get('http://localhost:3002/order_apply');

    return {
      sample: {
        data
      }
    };
  },
  created() {
    console.log('created');
    console.log(this);
  }
}
</script>

<style>
.container
{
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title
{
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
.subtitle
{
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
.links
{
  padding-top: 15px;
}
</style>
