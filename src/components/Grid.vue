
<template>
  <div class="grid-container">
    <div class="grid-thingie" v-for="grid in gridContent" @click="changeColors(grid)"  :style="{background: getColor(grid.style)}" :class="grid.class || null">
      <p>{{grid.text}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Grid',
  methods: {
    changeColors: function (grid) {
        if (grid.text) {
          this.colorOne = `#${Math.floor(Math.random()*16777215).toString(16)}`
          this.colorTwo = `#${Math.floor(Math.random()*16777215).toString(16)}`;
          this.colorThree = `#${Math.floor(Math.random()*16777215).toString(16)}`;
          this.colorFour = `#${Math.floor(Math.random()*16777215).toString(16)}`;
          this.colorFive = `#${Math.floor(Math.random()*16777215).toString(16)}`
          this.changeClasses()
        }
        return
    },
    changeClasses: function () {
      let classes = ['colorBase', 'colorBase', 'colorBase', 'colorOne', 'colorTwo', 'colorThree', 'colorFour', 'colorFive']
      this.gridContent.map(content => {
        if (content.text) return
        content.style = classes[Math.floor(Math.random()*classes.length)]
      })
    },
    getColor: function(style) {
      return this[style]
    }
  },
  data: function () {
    return {
      gridContent: [
        {
          style: 'colorBase'
        },
        {
          style: 'colorBase',
          class: 'span-two-column'
        },
        {
          style: 'colorBase'
        },
        {
          style: 'colorFour',
          class: 'span-two-row'
        },
        {
          style: 'colorBase'
        },
        {
          style: 'colorBase'
        },
        {
          class: 'span-two-row span-two-column',
          style: 'colorOne'
        },
        {
          class: 'white',
          text: 'click me for a surprise'
        },
        {
          class: 'span-three-row',
          style: 'colorBase'
        },
        {
          class: 'span-two-row',
          style: 'colorBase'
        },
        {
          style: 'colorThree'
        },
        {
          style: 'colorBase'
        },
        {
          style: 'colorBase'
        },
        {
          style: 'colorTwo'
        },
        {
          class: 'span-three-column',
          style: 'colorBase'
        },
        {
          style: 'colorThree'
        },
        {
          style: 'colorOne',
          class: 'span-two-column'
        }
      ],
      colorOne: '#36A58F',
      colorTwo: '#A84B59',
      colorThree: '#715C8E',
      colorFour: '#FBCAEF',
      colorFive: 'white',
      colorBase: 'white'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr 3fr 2fr 3fr 1fr;
  grid-template-rows: 30vh 19vh 14vh 34vh;
  grid-gap: 0.25rem;
  padding: 0.25rem;
  font-family: Arial, sans-serif;
}

.grid-thingie {
  background: white;
  display: grid;
  text-align: center;
  align-items: center;
}

.span-two-column {
  grid-column: span 2;
}

.span-two-row {
  grid-row: span 2;
}

.span-three-row {
  grid-row: span 3;
}

.span-three-column {
  grid-column: span 3;
}

.white {
  background: white;
  cursor: pointer;
}
</style>
