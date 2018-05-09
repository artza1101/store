<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <br>
    <div>
  <div class="columns">
  <div class="column"><a>Name Product : <input class="input is-small" type="text" placeholder="ชื่อสินค้า" v-model="name"></a></div>
  </div>

  <div class="columns">
    <div class="column"><a>Price Product : <input class="input is-small" type="text" placeholder="ราคาสินค้า" v-model="price"></a></div>
    </div>

  <div class="columns">
    <div class="column"><a>Number Product : <input class="input is-small" type="text" placeholder="จำนวนสินค้า" v-model="number"></a></div>
      </div>
  <button><a class="button" type="submit" @click="addproduct()">ตกลง</a></button>
</div>

</div>
</template>

<script>
import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyB-m9srs748X6ZpZyszv0KfKuvaNSf-2PE',
  authDomain: 'base-f994d.firebaseapp.com',
  databaseURL: 'https://base-f994d.firebaseio.com',
  projectId: 'base-f994d',
  storageBucket: 'base-f994d.appspot.com',
  messagingSenderId: '836623167018'
}
let app = firebase.initializeApp(config)
let db = app.database()
let store = db.ref('store')
export default {
  name: 'HelloWorld',
  firebase: {
    store: store
  },
  data () {
    return {
      msg: 'Product Store',
      name: '',
      price: '',
      number: ''
    }
  },
  methods: {
    addproduct () {
      let tmp = {
        name: this.name,
        price: this.price,
        number: this.number
      }
      store.push(tmp)
      this.name = ''
      this.price = ''
      this.number = ''
    },
    clear () {
      this.name = ''
      this.price = ''
      this.number = ''
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
