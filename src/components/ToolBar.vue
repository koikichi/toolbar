<template>
    <div class='toolbar-container'>
        <div class='toolbar-button-menu'>
            <button @click='togglePanel'>button1</button>
            <button @click='toggleItem2'>button2</button>
            <button @click='toggleItem1'>button3</button>
        </div>
      
        <!-- <div class='toolbar-panel' :style="css" v-if='show'>
            <div class='toolbar-panel-item-1'></div>
            <div class='toolbar-panel-item-2'></div>
        </div> -->
        <transition name='fade'>
            <!-- <div class='toolbar-panel-container' :style="css" v-if='show'> -->
                <div class='toolbar-panel-container' v-if='show'>
            <div class='toolbar-panel-item-1' v-if='showItem1'>1</div>
            <!-- <transition name='fade'> -->
            <div class='toolbar-panel-item-2' v-if='showItem2'>2</div>
            <!-- </transition> -->
            <div class='toolbar-panel-item-2'>3</div>
          
        </div>
        </transition>
        
    </div>
</template>

<script lang='ts'>
import Vue from 'vue';
export default Vue.extend({
  name: 'ToolBar',
  props: {},
  data() {
    return {
      show: false,
      css: {
        height: '0px',
      },
      showItem1: false,
      showItem2: false,
      showItem3: false,
    };
  },
  methods: {
    togglePanel() {
      this.show = !this.show;
      //   if (this.show) {
      //     this.css.height = '300px';
      //   } else {
      //     this.css.height = '0px';
      //   }
    },
    toggleItem1() {
      this.showItem1 = !this.showItem1;
    },
    toggleItem2() {
      this.showItem2 = !this.showItem2;
    },
  },
});
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.toolbar-panel-item-1 {
  min-height: 100px;
  width: 200px;
  /* background-color: yellow; */
  border-style: solid;
  border-color: black;
  border-radius: 10px;
  border-width: 4px;
  margin: 8px;
}

.toolbar-panel-item-2 {
  min-height: 200px;
  width: 400px;
  /* background-color: green; */
  border-style: solid;
  border-color: black;
  border-radius: 10px;
  border-width: 4px;
  margin: 8px;
  transition: 0.5s;
}

.toolbar-button-menu {
  display: flex;
  flex-direction: row;
  width: 98px;
  height: 40px;
}

.toolbar-panel-container {
  display: flex;
  flex-direction: column;
  /* grid-template-areas: '' */
  /* width: 100px; */
  max-height: 800px;
  overflow-y: auto;
  /* height: 500px; */
  /* background-color: blue; */
  transition: 0.5s;
  transition-delay: 0.1s;
}

/* .toolbar-panel ~ input:hover {
  height: 300px;
} */

.toolbar-container {
  position: fixed;
  display: flex;
  flex-direction: column;
  /* background-color: red; */
}
</style>