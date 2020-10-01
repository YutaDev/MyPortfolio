<template>
  <div class="home-page">
    <div class="banner">
      <div class="container">
        <h1 class="logo-font">MyPortfolio</h1>
        <p>私自身の成果物</p>
      </div>
    </div>
    <div class="container page">
      <div class="row">
        <div class="col-md-9">
          <div class="feed-toggle">
            <ul class="nav nav-pills outline-active">
              <li v-if="isAuthenticated" class="nav-item">
                <router-link
                  :to="{ name: 'home-my-feed' }"
                  class="nav-link"
                  active-class="active"
                >
                  Your Feed
                </router-link>
              </li>
              <li class="nav-item">
                <router-link
                  :to="{ name: 'home' }"
                  exact
                  class="nav-link"
                  active-class="active"
                >
                  プロフィール
                </router-link>
              </li>
              <li class="nav-item">
                <router-link
                  :to="{ name: 'skill' }"
                  exact
                  class="nav-link"
                  active-class="active"
                >
                  実績
                </router-link>
              </li>
              <li class="nav-item">
                <router-link
                  :to="{ name: 'output' }"
                  exact
                  class="nav-link"
                  active-class="active"
                >
                  成果物
                </router-link>
              </li>
              <li class="nav-item" v-if="tag">
                <router-link
                  :to="{ name: 'home-tag', params: { tag } }"
                  class="nav-link"
                  active-class="active"
                >
                  <i class="ion-pound"></i> {{ tag }}
                </router-link>
              </li>
            </ul>
          </div>
          <!--<router-view></router-view>-->
          <br /><br /><br />
          <ul>
            <li>
              <p>社外開発</p>
              <ul>
                <li>
                  <p>TodoList作成</p>
                </li>
              </ul>
              <p>社内新規開発</p>
              <ul>
                <li>
                  <p>Oracle専用テーブル設計書自動生成アプリケーション</p>
                </li>
                <li>
                  <p>業務サーバー全自動サーバ点検兼監視アプリケーション</p>
                </li>
              </ul>
            </li>
          </ul>
        </div>
        <div class="col-md-3">
          <div class="sidebar">
            <p>Popular Tags</p>
            <div class="tag-list">
              <RwvTag v-for="(tag, index) in tags" :name="tag" :key="index">
              </RwvTag>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import RwvTag from "@/components/VTag";
import { FETCH_TAGS } from "@/store/actions.type";

//外部で参照できるような宣言？？
export default {
  name: "home",
  components: {
    RwvTag
  },
  mounted() {
    this.$store.dispatch(FETCH_TAGS);
  },
  //ヘルパーはストアのゲッターをローカルの算出プロパティにマッピングさせる
  //状態を呼び出す？？
  ...mapGetters(["isAuthenticated", "tags"]),
  tag() {
    return this.$route.params.tag;
  }
};
</script>
