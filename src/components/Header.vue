<template>
<div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-brand to="/">StockApp</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item to="/portfolio">Portfolio</b-nav-item>
        <b-nav-item to="/stocks">Stocks</b-nav-item>
        <!-- <router-link to="/portfolio" tag="li" active-class="active"><a>Portfolio</a></router-link> -->
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-item to="#" class="active"><strong>Funds:({{funds | currency}})</strong></b-nav-item>
        <b-nav-item to="#" @click="endDay">End Day</b-nav-item>
        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template v-slot:button-content>
            Save & Load
          </template>
          <b-dropdown-item @click="saveData">Save</b-dropdown-item>
          <b-dropdown-item @click="loadBData">Load</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
</template>

<script>
import {mapActions} from 'vuex'
    export default {
        computed:{
            funds(){
                return this.$store.getters.funds
            }
        },
        methods:{
          ...mapActions([
            'randomizeStocks',
            'loadData'
          ]),
          endDay(){
            this.randomizeStocks()
          },
          saveData(){
            const data = {
              funds: this.$store.getters.funds,
              stockPortfolio: this.$store.getters.stockPortfolio,
              stocks: this.$store.getters.stocks
            };
            this.$http.put('data.json', data)
          },
          loadBData(){
            this.loadData();
          }
        }
    }
</script>