<template>
  <h2>Full Name: {{firstName}} {{lastName}}</h2>
  <h2>Computed Full Name: {{fullName}}</h2>

  <button @click="changeFullName">Chage Fullname</button>

  <button @click="items.push({id: 4, title:'Car', price: 1000})">Add Item</button>
  <h2>Total: {{total}} </h2>

  <template v-for="item in items" :key="item.id">
    <h2 v-if="item.price > 100">{{item.title}}: {{item.price}}</h2>
  </template>

  <h2 v-for="item in expensiveItems" :key="item.id">
    {{item.title}}: {{item.price}}
  </h2>

  <h2>Volume: {{volume}}</h2>
  <button @click="volume += 2">Increase Volume</button>
  <button @click="volume -= 2">Decrease Volume</button>

  <input type="text" v-model="name" />

  <input type="text" v-model="movieInfo.actor" />
  <input type="text" v-model="movieInfo.title" />

</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      firstName: 'Bruce',
      lastName: 'Wayne',
      name: 'Batman',
      items: [
        {
          id: 1,
          title: 'TV',
          price: 100
        }, 
        {
          id: 2,
          title: 'Phone',
          price: 70
        },
        {
          id: 3,
          title: 'medicine',
          price: 300
        },
      ],
      volume: 0,
      movieInfo: {
        actor: '',
        title: '',
      }
    }
  },
  methods: {
    changeFullName() {
      this.fullName = 'Clark Kent';
    }
  },
  computed: {
    fullName: {
      get() {
        return `${this.firstName} ${this.lastName}`;
      },
      set(value) {
        [this.firstName, this.lastName] = value.split(' ');
      }
    },
    total() {
      return this.items.reduce( (total, current) => total += current.price, 0);
    },
    expensiveItems() {
      return this.items.filter( item => item.price > 100 );
    }
  },
  watch: {
    volume(newValue, oldValue) {
      if( newValue > oldValue && newValue === 16 ) {
        alert('Volume too high!');
      }
    },
    name: {
      handler(newValue) {
      console.log(`Api with ${newValue}`);
      },
      immediate: true,
    },
    movieInfo: {
      handler(newValue) {
        console.log(`Api with actor: ${newValue.actor} title: ${newValue.title}`);
      },
      deep: true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

.underline {
  text-decoration: underline;
}
.promoted {
  font-style: italic;
}
.new {
  color: olivedrab;
}
.sold-out {
  color: red;
}
label {
  font-weight: bold;
  display: flex;
  margin-bottom: 5px;
}
input + label {
  font-weight: bold;
  display: inline-flex;
  margin-right: 20px;
}
input[type='text'],
textarea,
select {
  display: block;
  width: 400px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 4px;
}

</style>
