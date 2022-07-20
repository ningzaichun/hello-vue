<template>
  <!--  所有的元素必须在根节点下-->
  <div>
    <h1>个人信息</h1>
    <!--在要展示的组件Profile.vue中接收参数 使用 {{$route.params.id}}来接收-->
    {{id}}
  </div>
</template>

<script>
  export default {
    props: ['id'],
    //第二种取值方式
    // props:['id'],
    name: "UserProfile",
    //钩子函数 过滤器
    beforeRouteEnter: (to, from, next) => {
      //加载数据
      console.log("进入路由之前")
      next(vm => {
        //进入路由之前执行getData方法
        vm.getData()
      });
    },
    beforeRouteLeave: (to, from, next) => {
      console.log("离开路由之前")
      next();
    },
    //axios
    methods: {
      getData: function () {
        this.axios({
          method: 'get',
          url: 'http://localhost:8081/hello'
        }).then(function (response) {
          alert(response);
          console.log(response)
        })
      }
    }
  }
</script>
<style scoped>
</style>
