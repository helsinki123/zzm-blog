<template>
  <div class="view_box" @scroll="scroll" id="view_box">
    <div id="scroll_box" :style="{'height':`${total}px`}">
      <div class="absolute_box" :style="{'position': 'absolute','top':`${scrollTop}px`}">
        <div v-for="item in itemList" :key="item" class="item">
          {{ item }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      itemList: [],
      list: [],
      startIndex:0,
      endIndex:0,
      top:0,
      itemHeight:20,
      scrollTop:0,
      total:0
    };
  },
  mounted(){
    this.getList();
    this.total = 20*(this.list.length);
    this.scroll();
  },
  methods: {
    getList() {
      for (let i = 0; i < 100; i++) {
        this.list.push(`zzm${i}`);
      }
    },
    scroll(){
        console.log("111");
        this.startIndex = this.scrollTop/this.itemHeight;
        this.endIndex = Math.min(this.startIndex+10,this.total-1);
        this.itemList = this.list.slice(this.startIndex,this.endIndex);
        
        this.scrollTop = document.getElementById("view_box").scrollTop;
        console.log(this.scrollTop);
        this.top = this.scrollTop;
    }
  },
};
</script>

<style>
.view_box{
  overflow: auto;
  width: 500px;
    height: 200px;
    border: 1px solid red;
}
#scroll_box{
    position: relative;
}
.absolute_box{
    
    color: red;
}
.item{
    height: 20px;
}
</style>
