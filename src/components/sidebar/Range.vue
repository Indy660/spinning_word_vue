<template>
 <div class="range">
    <input
        type="range"
        :min="min" :max="max"
        step="1"
        v-model="inputModel"
    >
    <div class="numbers">
      <div class="min">{{ min }}</div>
      <div class="data">{{ inputModel }}</div>
      <div class="max">{{ max }}</div>
    </div>
 </div>
</template>

<script>
 export default {
   name: 'Range',
   props: {
     stateProp: {
       type: Array,
       default: () => [],
     },
     action: {
       type: String,
       default: ''
     },
     min: {
       type: Number,
       default: 0,
     },
     max: {
       type: Number,
       default: 100,
     },
   },
   computed: {
     inputModel: {
       get () {
         let path = this.$store.state
         return this.stateProp.reduce((current, key) => current?.[key], path)
       },
       set (value) {
         // setTimeout(() => this.$store.commit(this.action,  parseInt(value)), 300);
        this.$store.commit(this.action,  parseInt(value));
       }
     }
   },
 }
</script>

<style scoped>
  input[type=range] {
    -webkit-appearance: none;
    display: block;
    width: 100%;
    margin: 16px 0;
    background-image: linear-gradient(to right, #ADD8E6 0%,#00c0ff 100%);
    background-repeat: no-repeat;
  }
  input[type=range]:focus {
    outline: none;
  }
  input[type=range]::-webkit-slider-runnable-track {
    width: 100%;
    height: 4px;
    cursor: pointer;
    box-shadow: none;
    background: transparent;
    border: none;
  }
  input[type=range]::-webkit-slider-thumb {
    box-shadow: none;
    border: 4px solid #ADD8E6;
    height: 16px;
    width: 16px;
    border-radius: 2px;
    background: #3e3e3f;
    cursor: pointer;
    -webkit-appearance: none;
    margin-top: -6px;
  }
  input[type=range]:focus::-webkit-slider-runnable-track {
    background: transparent;
  }
  input[type=range]::-moz-range-track {
    width: 100%;
    height: 4px;
    cursor: pointer;
    box-shadow: none;
    background: transparent;
    border: none;
  }
  input[type=range]::-moz-range-thumb {
    box-shadow: none;
    border: 4px solid #ADD8E6;
    height: 16px;
    width: 16px;
    border-radius: 2px;
    background: #ffffff;
    cursor: pointer;
  }
  input[type=range]::-ms-track {
    width: 100%;
    height: 4px;
    cursor: pointer;
    background: transparent;
    border-color: transparent;
    color: transparent;
  }
  input[type=range]::-ms-fill-lower {
    background: transparent;
    border: none;
    box-shadow: none;
  }
  input[type=range]::-ms-fill-upper {
    background: transparent;
    border: none;
    box-shadow: none;
  }
  input[type=range]::-ms-thumb {
    box-shadow: none;
    border: 4px solid #ADD8E6;
    height: 16px;
    width: 16px;
    border-radius: 2px;
    background: #ffffff;
    cursor: pointer;
  }
  input[type=range]:focus::-ms-fill-lower {
    background: transparent;
  }
  input[type=range]:focus::-ms-fill-upper {
    background: transparent;
  }
  .numbers {
    display: flex;
    justify-content: space-around;
  }
  .numbers .data {
    font-size: 20px;
  }
  .numbers .min, .numbers .max {
    margin: 0 10px;
  }
</style>