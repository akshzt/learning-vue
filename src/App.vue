<template>
  <div>{{ greet }} {{ name }}</div>
  <div v-text="color"></div>
  <div v-html="colorHtml"></div>
  <div v-html="alertRandom"></div>
  <div v-bind:id="headingId">Heading</div>
  <button v-bind:disabled="isDisabled">Button</button>
  <h2 class="underline">Underlined text</h2>
  <h2 class="underline" v-bind:class="status">Status</h2>
  <h2 v-bind:class="isPromoted && 'promoted'">Promoted Movie</h2>
  <h2 v-bind:class="isSoldOut ? 'sold-out' : 'new'">Sold Out</h2>
  <h2 v-bind:class="['new', 'promoted']">Newly Promoted Movie</h2>
  <h2 v-bind:class="[isPromoted && 'promoted', isSoldOut ? 'sold-out' : 'new']">Array Conditional Movie</h2>
  <h2 v-bind:class="{
    promoted: isPromoted,
    new: !isSoldOut,
    'sold-out': isSoldOut,
  }">
    Object Conditional Movie
  </h2>

  <h2 v-bind:style="{
    color: highlightColor,
    padding: '20px',
    fontSize: headerSize + 'px',
    'font-size': headerSize + 'px',
  }">Inline Style</h2>

  <h2 v-bind:style="headerStyleObject">Style Object</h2>

  <div v-bind:style="[baseStyleObject, successStyleObject]">Success Style</div>
  <div v-bind:style="[baseStyleObject, dangerStyleObject]">Danger Style</div>

  <div :style="[dangerStyleObject]">Danger Style 2</div>

  <h2 v-if="num >= 0">The number is positive</h2>
  <h2 v-else-if="num < 0">The number is negative</h2>
  <h2 v-else>Not a number</h2>

  <!-- <div v-if="displayFalse">
    <h2>Display</h2>
    <h2>is</h2>
    <h2>True</h2>
  </div> -->

  <template v-if="displayTrue">
    <h2>Display</h2>
    <h2>is</h2>
    <h2>True</h2>
  </template>

  <h4 v-show="showElement">show element, v-show, use when toggling with display, v-if mounts/unmounts from dom, v-show does display: none</h4>

  <h2 v-for="(name, index) in names" :key="name">{{index}}: {{name}}</h2>

  <h2 v-for="name in fullNames" :key="name.first">{{name.first}} {{name.last}}</h2>

  <div v-for="actor in actors" :key="actor.name">
    <h2>{{actor.name}}</h2>
    <h3 v-for="(movie, index) in actor.movies" :key="index">{{index}}: {{movie}}</h3>
  </div>

  <h2 v-for="(value, key, index) in myInfo" :key="value">{{index}}: {{key}}: {{value}}</h2>

  <template v-for="name in names" :key="name">
    <h2 v-if="name === 'Bruce'">{{name}}</h2>
  </template>

  <template v-for="name in names" :key="name">
    <h2>{{name}}</h2>
    <hr />
  </template>

  <h2>Add Method: {{add(2, 3, 5)}}</h2>
  <h2>Multiply Method: {{multiply(2)}}</h2>

</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      greet: 'Hello',
      name: 'SomeName',
      color: 'Purple',
      colorHtml: '<b>Red</b>',
      alertRandom: `<a href="#" onclick="alert('Clicked on this!')">Click here</a>`,
      headingId: 'heading',
      isDisabled: true,
      status: 'danger',
      isPromoted: true,
      isSoldOut: true,
      highlightColor: 'orange',
      headerSize: 50,
      headerStyleObject: {
        color: 'orange',
        fontSize: '50px',
        padding: '20px',
      },
      baseStyleObject: {
        fontSize: '50px',
        padding: '10px',
      },
      successStyleObject: {
        color: 'green',
        backgroundColor: 'lightgreen',
        border: '1px solid green',
        padding: '20px',
      },
      dangerStyleObject: {
        color: 'darkred',
        backgroundColor: 'red',
        border: '1px solid darkred',
      },
      num: 'abc',
      displayTrue: true,
      displayFalse: false,
      showElement: true,
      names: ['Bruce', 'Clark', 'Diana'],
      fullNames: [
        { first: 'Bruce', last: 'Wayne' },
        { first: 'Clark', last: 'Kent' },
        { first: 'Princesss', last: 'Diana'},
      ],
      actors: [
        {
          name: 'Christian Bale',
          movies: ['Batman', 'The Prestige'],
        },
        {
          name: 'Leonardo Di Caprio',
          movies: ['Titanic', 'Inception'],
        },
      ],
      myInfo: {
        name: 'someName',
        color: 'pink',
        course: 'Vue 3',
      },
      baseMultiplier: 5,
    };
  },
  methods: {
    add(a, b, c) {
      return a + b + c;
    },
    multiply(num) {
      return num * this.baseMultiplier;
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
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

</style>
