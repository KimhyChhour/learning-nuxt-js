<template>
  <div>
    <section class="heading">
      <h1>Most Popular Rivers In the World</h1>
      <p>
        Photo Credits:
        <a href="https://wikimedia.org">wikimedia.org</a>
      </p>
    </section>
    <section class="grid">
      <div
        class="grid-item"
        v-for="(river, index) in rivers"
        :key="`river-${index}`"
      >
        <img :src="river.image" :alt="river.title"/>
        <p><b>{{ river.title }}</b>, Length: {{ river.length }}, Countries: {{ river.countries}}, Continent: {{ river.continent }}</p>
      </div>
    </section>
    <!-- <h3>Hello World</h3>
    <button v-tooltip="'This is our button'">Button</button> -->
  </div>
</template>

<script>
import 'floating-vue/dist/style.css'
export default {
  name: 'IndexPage',
  // head: {
  //   meta: [
  //     {
  //       hid: 'title',
  //       content: 'Home Page'
  //     },
  //     {
  //      hid: 'description',
  //      content: 'This is the Home Page'
  //     },
  //   ]
  // },

  head () {
    return {
      meta: [
        {
          hid: 'title',
          content: 'Home Page'
        },
        {
        hid: 'description',
        content: 'This is the Home Page'
        },
      ]
    }
  },

  data () {
    return {
      rivers: []
    }
  },

  // async asyncData ({ $http}) {
  //   // https://api.nuxtjs.dev/rivers
  //   const res = await $http.$get('https://api.nuxtjs.dev/rivers')
  //   // console.log(res)
  //   return {
  //     rivers: res
  //   }
  // }

  async fetch () {
    const res = await this.$http.$get('https://api.nuxtjs.dev/rivers')
    this.rivers = res
  }
}
</script>

<style>
body {
  margin: 0 auto;
  border: 10px solid #6a5acd;
}

.heading {
  text-align: center;
  padding: 20px;
  font-size: 20px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  margin: 0 30px;
}

.grid-item {
  border-radius: 5px;
  height: 300px;
  cursor: pointer;
  margin: 4px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -30px, rgba(0, 0, 0, 0.3) 0px 30px 60px -40px;
}

.grid-item img {
  width: 100%;
  height: 80%;
  object-fit: cover;
  border-radius: 2px;
}

.grid-item p {
  margin: 0 auto;
  text-align: center;
  font-size: 12px;
  padding: 5px;
}

.grid-item:hover {
  box-shadow: rgba(22, 18, 13, 0.501) 0px 4px 12px;
}

@media screen and (min-width: 481px) {
  .grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 10px;
  }
}

@media screen and (min-width: 769px) {
  .grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 10px;
  }
}
</style>
