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
    'font-size': headerSize + 'px',
  }">Inline Style</h2>

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
    };
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
