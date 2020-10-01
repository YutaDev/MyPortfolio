<template>
  <div class="home-page">
    <div class="banner">
      <div class="container">
        <h1 class="logo-font">MyPortfolio</h1>
        <p>私自身の実績</p>
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
          <router-view></router-view>
          <br><br><br><br>
          <p>私が培ってきた主な実績を紹介します</p>
          <ul>
            <li><p>法律改正に伴う婦人科検診アプリケーション改修</p></li>
              <p>開発期間：2019年12月〜2020年03月</p>
              <p>開発規模：4人</p>
              <p>
                開発環境：
                <ul>
                  <li>
                  OS：Windows Server2012
                  </li>
                  <li>
                  DB(バックエンド)：OracleDB 12c
                  </li>
                  <li>
                    フロントエンド：.NetFramework C#
                  </li>
                  <li>
                    ツール：Visual Studio2017
                 </li>
                </ul>
              </p>
              <p>
                担当部分：
                基本設計・詳細設計・コーディング・テスト・リリース
              </p>
              <br><br><br>
              <li><p>特定保健指導システム評価時季変更に伴う改修</p></li>
              <p>開発期間：2018年12月〜2020年05月</p>
              <p>開発規模：4人</p>
              <p>
                開発環境：
                <ul>
                  <li>
                  OS：Windows Server2012
                  </li>
                  <li>
                  DB(バックエンド)：OracleDB 12c
                  </li>
                  <li>
                    フロントエンド：.NetFramework C#
                  </li>
                  <li>
                    ツール：Visual Studio2017
                 </li>
                </ul>
              </p>
              <p>
                担当部分：
                基本設計・詳細設計・コーディング・テスト・リリース
              </p>
              <br><br><br>
              <li><p>OracleDB 保守運用</p></li>
              <p>開発期間：2018年06月〜2020年09月</p>
              <p>対応規模：1人</p>
              <p>
                開発環境：
                <ul>
                  <li>
                  OS：Windows Server2012
                  </li>
                  <li>
                  DB：OracleDB 12c
                  </li>
                  <li>
                    ツール：PL/SQL Developer
                 </li>
                </ul>
              </p>
              <p>
                担当部分：
                障害発見・原因究明・障害対応(恒久的対応)
              </p>
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
