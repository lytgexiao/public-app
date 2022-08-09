<template>
  <div class="home">
    <h3>这里是父应用内容，父应用router-view 被keep-alive包含</h3>
     <strong>希望切换父应用路由，父子应用的页面都保留状态</strong>
     <br/>
     <br/>
    <input />
    <micro-app
      name="page1"
      url="http://localhost:8080/"
      :baseroute="'/home'"
      :data="pageData"
      keep-alive
      inline
      @datachange="handleDataChange"
    ></micro-app>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "HomeView",
  data() {
    return {
      pageData: {
        pageId: "page1",
        setting: {
          globalDataTakeOver: true,
        },
        layout: "",
        env: {},
      },
    };
  },
  components: {},
  created() {
    let layout1 = {
      type: "e-page",
      body: [{ type: "e-button", btnText: "按钮12" }],
    };
    let layout2 = { type: "e-page", body: [{ type: "e-text" }] };
    this.pageData.layout = JSON.stringify(layout2);
    console.log(999999999, this.pageData);
  },
  methods:{
    handleDataChange(){

    }
  }
};
</script>
