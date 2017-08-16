<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i}" v-on:click="currentTab = i">
            <svg class="icon" aria-hidden="true">
              <use v-bind:xlink:href="'#icon-${icons[i]}`"></use>
            </svg>
        </li>
      </ol>
    </nav>
    <ol class="panels">
      <li v-bind:class="{active: currentTab === 0}">tab0</li>
      <li v-bind:class="{active: currentTab === 1}">tab1</li>
      <li v-bind:class="{active: currentTab === 2}">tab2</li>
      <li v-bind:class="{active: currentTab === 3}">tab3</li>
      <li v-bind:class="{active: currentTab === 4}">tab4</li>
      <li v-bind:class="{active: currentTab === 5}">tab5</li>
    </ol>
  </div>
</template>

<script>
export default {
  data(){
    return{
      currentTab:0,
      icons:['xinxi','xueli','jiangli2','xingquaihao','jishu1','02']
    }
  }
}
</script>


<style lang='scss'>
#editor{
  display: flex;
  min-height: 100px;
  nav {
    background: #000;
    width: 80px;
    ol li{
      text-align: center;
      padding: 16px 0;
      .icon {
        width: 24px;
        height: 24px;
        fill: #fff;
      }
      &.active{
        background: #fff;
        .icon{
          fill: #000;
        }
      } 
    }
  }
  .panels{
    flex: 1;
    li{
      display: none;
      &.active{
        display: block;
      }
    }
  }
}

</style>