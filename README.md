## es6高大上遍历json

`Object.keys(filters).forEach(key => Vue.filter(key, filters[key]))`

## 在线小工具
#### [color](http://tools.jb51.net/color/jPicker) [reg](http://tools.jb51.net/regex/create_reg) [other online tools ](http://tools.jb51.net/code)
## 日常生活中可能用到的命令和模板
### node.js环境搭建
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install vue-cli -g
```
### 模板
#### sport.vue
```

<template lang="html">
  <div>
    I am sport
  </div>
</template>

<script>
export default {
}
</script>

<style lang="stylus">
div:hover
 color red
</style>

```
#### main.js
```

// The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
import Vue from 'vue'
import App from './App'
import routes from './routes'
import ElementUI from 'element-ui'
import vueResource from 'vue-resource'
import 'element-ui/lib/theme-default/index.css'
import VueRouter from 'vue-router'
import store from './store1/index'
import Loadings from './components/loading'
import Loadingss from './components/loading/index1'
require('./assets/css/base.css')
/* 全局引入base文件 */
Vue.use(Loadings)
Vue.use(Loadingss)
Vue.use(VueRouter)
Vue.use(vueResource)
const router = new VueRouter({
  mode: 'history',
  /* 切换路劲模式，变成history模式 */
  scrollBehavior: () => ({
    y: 0
  }),
  /* 滚动条滚动行为，不加这个就会默认记忆原来滚动条的位置 */
  routes
})
Vue.use(ElementUI)
Vue.config.productionTip = false
/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  store,
  template: '<App/>',
  components: { App }
})

```
#### routes.js
```

import Hello from './components/Hello'
import News from './components/news'
import Sports from './components/sports'
const routes = [
  {path: '/news', component: News},
  {path: '/sports', component: Sports},
    {path: '/', component: Hello},
    {path: '*', redirect: '/'}
]
export default routes

```
#### app.vue
```

<template>
  <div id="app">
    {{num}}

    <loading v-show="show"></loading>
    <input type="button" name="" value="点击增加" @click='increment'>
    <input type="button" name="" value="点击减少" @click="decrement">
    <input type="button" name="" value="只有偶数才能点击+" @click="clickOdd">
    <input type="button" name="" value="异步增加" @click="clickAsync">

      <p>现在的数字是:{{count}},他是{{odd}}</p>
    <el-button type="primary" icon="search">搜索</el-button>
    <img src="./assets/logo.png">
    <router-link to='/news'>news</router-link>
    <router-link to='/sports'>sports</router-link>
    <div>
      <router-view></router-view>
    </div>
    <v-header></v-header>
    <router-view></router-view>
    <div class="">
      {{seller}}
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import Header from './components/header'
export default {
  name: 'app',
  watch: {
    $route (to, from) {
      console.log(to.path)
      if (to.path === '/news') {
        this.$store.dispatch('hideHeader')
      } else {
        this.$store.dispatch('showHeader')
      }
    }
  },
  components: {
    'v-header': Header
  },
  data () {
    return {
      goods: {},
      seller: {},
      rating: {},
      num: 0
    }
  },
  computed: mapGetters([
    'count',
    'odd',
    'show',
    'num'
  ]),
  methods: mapActions([
    'increment',
    'decrement',
    'clickOdd',
    'clickAsync',
    'showHeader',
    'hideHeader',
    'change'
  ]),
  created () {
    // this.change()
  // GET /someUrl
    this.$http.get('api/goods').then(response => {
    // get body data
       this.goods = response.body
    }, response => {
    console.log('数据还未获取到')
    })
    this.$http.get('api/seller').then(response => {
    // get body data
       this.seller = response.body
    }, response => {
    console.log('数据还未获取到')
    })
    this.$http.get('api/goods').then(response => {
    // get body data
       this.goods = response.body
    }, response => {
    console.log('数据还未获取到')
    })
}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```
### store
#### actions.js
```
export default {
  increment: ({commit}) => {
    commit('increment')
  },
  decrement({commit}) {
    commit('decrement')
  },
  clickOdd({commit, state}) {
    if (state.mutations.count % 2 === 0) {
      commit('increment')
    }
  },
  clickAsync({commit}) {
    return new Promise((resolve) => {
      setTimeout(() => {
        commit('increment')
      }, 1000)
    })
  },
  showHeader({commit}) {
    commit('showHeader')
  },
  hideHeader({commit}) {
    commit('hideHeader')
  },
  change({commit}) {
    commit('change')
  }
}

```
#### mutations.js
```
import getters from './getters'
const state = {
  count: 10,
  show: true,
  num: 0
}
const mutations = {
  increment(state) {
    state.count++
  },
  decrement(state) {
    state.count--
  },
  showHeader(state) {
    state.show = true
  },
  hideHeader(state) {
    state.show = false
  },
  change(state) {
    state.num = 1
  }
}
export default {
  state,
  mutations,
  getters
}

```
### getters.js
```
export default {
  count: (state) => state.count,
  odd: (state) => state.count % 2 === 0 ? '偶数' : '奇数',
  show: (state) => state.show,
  num: (state) => state.num
}
```
### index.js
```
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)

import mutations from './mutations'
import actions from './actions'

export default new Vuex.Store({
  modules: {
    mutations
  },

  actions

})

```
