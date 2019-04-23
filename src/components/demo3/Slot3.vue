<template>
  <div class="father">
    <h3>这里是父组件</h3>
    <!--我的注释:该页面现在只有样式了,数据在child组件里定义,该页面获取child组件里的数据并渲染,slot-scope应该是用于获得slot并给一个命名,然后通过该slot命名->slot里的属性名就可以获取slot里对应的数据-->
    <!--第一次使用：用flex展示数据-->
    <child>
      <template slot-scope="copy1">
        <div class="tmpl">
          <span v-for="item in copy1.data2">{{item}}</span>
        </div>
      </template>

    </child>

    <!--第二次使用：用列表展示数据-->
    <child>
      <template slot-scope="copy2">
        <ul>
          <li v-for="item in copy2.data2">{{item}}</li>
        </ul>
      </template>

    </child>

    <!--第三次使用：直接显示数据-->
    <child>
      <template slot-scope="copy3">
       {{copy3.data2}}
      </template>

    </child>

    <!--第四次使用：不使用其提供的数据-->
    <child>
      我就是模板
    </child>
  </div>
</template>

<script>
  import Child from './Child.vue'
  export default {
    data: function () {
      return {
        msg: ''
      }
    },
    methods: {
      clickHandler(data){
          console.log(data);
      }
    },
    components:{
      'child': Child
    }
  }
</script>

<style scoped>
  .father{
    width:100%;
    background-color: #ccc;
    height: 650px;
  }
  .tmpl{
    display: flex;
    justify-content: space-around;
    flex-direction: row;
    width: 30%;
    margin: 0 auto;
  }
  .tmpl span{
    border:1px solid red;
    height:50px;
    line-height: 50px;
    padding: 10px;
  }
</style>
