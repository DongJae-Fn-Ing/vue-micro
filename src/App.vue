<template>
  <div class="wrap">
    <div class="sub-wrap">
      <LeftMenu :MenuData="MenuData" :UserData="UserData" :MenuOnF="MenuOnF" />
      <div class="main" :class="{ on: MenuOnF === false }">
        <Header :MenuOnF="MenuOnF" @MenuChange="MenuOnF = $event" />
        <div class="content">
          <router-view :TabData="TabData"></router-view>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "../public/global.css";
import LeftMenu from "./components/LeftMenu";
import Header from "./components/Header";

/* 더미 데이터 */
import MenuData from "./assets/data/menu";
import UserData from "./assets/data/user";
import TabData from "./assets/data/tabData";

export default {
  name: "App",
  data() {
    return {
      MenuData: MenuData,
      UserData: UserData,
      LoginData: "",
      MenuOnF: true,
      TabData: TabData,
    };
  },
  methods() {},
  mounted() {},
  components: {
    LeftMenu,
    Header,
  },
};
</script>

<style>

.wrap {
  position: relative;
  width: 100%;
  height: 100%;
}

.sub-wrap {
  display: flex;
  width: 100%;
  height: 100%;
}

.sub-wrap .main {
  width: calc(100% - 242px);
  margin-left: 242px;
  transition: all 0.3s ease-in-out;
}

.sub-wrap .main.on {
  width: 100%;
  margin-left: 0;
}

.sub-wrap .main .content {
  display: flex;
  width: 100%;
  height: 100%;
  padding: 20px 40px 0;
  flex-wrap: wrap;
  gap: 0 30px;
}

.content .content-box {
  width: 100%;
  height: 100%;
  border: 1px solid #ddd;
  border-radius: 4px;
  background-color: #fff;
}

.inner-box {
  width: 100%;
  height: 100%;
  border: 1px solid #ddd;
  border-radius: 4px;
  background-color: #fff;
}

.inner-box .detail-title {
  display: flex;
  height: 100px;
  padding: 0 20px;
  border-bottom: 1px solid #ddd;
  align-items: center;
  justify-content: space-between;
}

.inner-box .detail-title h3 {
  font-size: 28px;
}

.inner-box .detail-content {
  padding: 20px;
  min-height: 630px;
}

@media (max-width: 768px){
  .sub-wrap .main{
    width: 100%;
    margin-left: 0;
  }
}
</style>
