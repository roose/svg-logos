<template>
  <div class="content">
    <div class="search-wrapper">
      <input type="text" v-model="search" placeholder="Search title.."/>
    </div>
    <ul>
      <li v-for="item in filteredList">
        <a href="" :href="item.url">
          <!-- <img src="" :src="'static/logos/' + item.file" alt=""> -->
          <img :src="'../logos/'+ item.file" alt="">
        </a>
        <div class="desc">
          <h4>{{item.name}}</h4>
          <span>{{item.category}}</span>
        </div>
      </li>
    </ul>
  </div>
  <!-- /.content -->
</template>

<script>
import json from '../../logos.json'
export default {
  name: 'hello',
  data () {
    return {
      search: '',
      logoList: json.items
    }
  },
  computed: {
    filteredList () {
      return this.logoList.filter(logo => {
        return logo.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  }
}
</script>

<style scoped>
  ul {
    list-style-type: none;
    display: flex;
    justify-content: space-between;
    margin: 0;
    padding: 0;
  }
  li {
    width: 32%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    padding: 60px 30px 120px 30px;
    position: relative;
  }
  a {
    width: 100%;
    margin-top: 30px;
    margin-bottom: 30px;
  }
  img {
    width: 90%;
    height: auto;
  }
  .desc {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    text-align: center;
  }
</style>