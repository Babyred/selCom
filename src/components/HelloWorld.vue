<template>
<div class="content" >
  <div class="select"  ref="selected" @click="isSelected">
    <input type="text" disabled placeholder="请选择">
    <div class="point">
    </div>
  </div>
  <div class="options" v-if="show">
    <ul>
      <li v-for="item in options" :key="item.value">
        <input type="checkbox" v-model="selected" :id="item.value" :value="item"> 
        <label :for="item.value">{{item.label}}</label>  
      </li>
    </ul>
  </div>
  <div class="selected" v-if="selected.length">
    <div class="tag" v-for="item in selected" :key="item.value">
      {{item.label}}
       <span class="close" @click="closed(item)">X</span>
    </div>

  </div>
</div>

</template>

<script>
  export default {
    data() {
      return {
        show: false,
        options: [{
          value: '选项1',
          label: '黄金糕'
        }, {
          value: '选项2',
          label: '双皮奶'
        }, {
          value: '选项3',
          label: '蚵仔煎'
        }, {
          value: '选项4',
          label: '龙须面'
        }, {
          value: '选项5',
          label: '北京烤鸭'
        }],
        selected: [],
      }
    },
    methods:{
      isSelected() {
        this.show = !this.show;
        console.log(this.$refs.selected.className.indexOf("isfoucs"))
        if (!(this.$refs.selected.className.indexOf("isfoucs")+1)) {
          this.$refs.selected.className += ' isfoucs';
        }else {
          this.$refs.selected.className = 'select';
        }
      },
      // hover() {
      //   console.log("a");
      // },
      closed(key) {
        this.selected.splice(this.selected.indexOf(key),1);
      }
    }
  }

</script>
<style>
.content {
  display: inline-block;
  position: relative;

}
.select {
  border: 1px solid #aaaaaa;
  border-radius: 10px;
  padding:5px;
  display: inline-block;
 
}
.select input {
  border: none;
  cursor: pointer;
  background: #fff;
}
.selected {
  position: absolute;
  top: 0;
  padding:5px;
   z-index: 0;
}
.isfoucs {
  border-color: #409EFF;
}
.options {
  display: inline-block;
  position: absolute;
  left: 0;
  top: 32px;
  width: 100%;
  border: 1px solid #aaaaaa;
  border-radius: 10px;
  background: #ffffff;
}
ul {
  list-style: none;
  padding: 5px;
}
li {
  cursor: pointer;
}
.tag {
  display: inline-block;
  background: #409EFF;
  color: #fff;
  font-size: 10px;
  margin-left: 2px;
  padding: 5px;
  border-radius: 5px;
}
.close {
  margin-left: 4px;
  cursor: pointer;
}
</style>
