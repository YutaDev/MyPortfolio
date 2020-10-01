<template>
  <div class="home-page">
    <div class="banner">
      <div class="container">
        <h1 class="logo-font">MyPortfolio</h1>
        <p>私自身の紹介</p>
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
          <!--<router-view></router-view> -->
          <br /><br /><br /><br />
          <p>こんにちは。宮野優大と申します。</p>
          <ul>
            <li>学歴</li>
            <p>
              <br>新潟県立新発田南高等学校 電子情報工学科 2016年03月　卒業
            </p>
            <p>新潟職業能力開発短期大学校 電子情報技術科 2018年03月 卒業</p>
            <p>株式会社アイ・ピー・ピー　2018年04月 入社</p>
          </ul>

          <p>
            高校、大学共に、情報系の学科でプログラミングの他、サーバーやネットワークなどの周辺技術を学び、卒業論文ではDeep
            Learning技術による
            動物の認識アプリや、手書き名前文字認識アプリを実装し、Deep
            Learningへの理解を深めました。
          </p>
          <p>
            卒業後、東京都の独立系Slerに就職し、システムエンジニアとして、約2年半、健康保険組合系の業務システムを設計、開発、テスト、リリースを一人称で担当。
            及び、データベース管理者として同現場の業務システムのOracleDB、Windows
            Serverの保守、運用を一人称で担当。
            また、複数人(四人)のプロジェクトのリーダーとして、設計、開発を担当し、経験が浅いエンジニアに対する技術教育担当も担当。
          </p>
          <ul>
            <li>
              社外での活動
            </li>
            <p>
              2018年度
              IT系の勉強会を勉強会マッチングアプリCommpassを使ってモダンな言語の勉強会に多々足を運ぶ。
              主な内容は、C#やOracleなどの現場で使う技術
            </p>
            <p>
              2019年度
              同じく、Commpassやその他SNSで勉強会のメンバーを募り、今度はモダンな言語の分野を学ぶ。
              Vue.jsやGo、Docker、AWSなど...
            </p>
            <p>
              2020年度
              DiscordやZoomなどの通信アプリで、勉強会を開催し、エンジニア達との勉強及び交流を図った。
            </p>
          </ul>
          <ul>
            <li>学んできた言語</li>
            <p><br />.Net Framework</p>
            <p>Entity Framework</p>
            <p>Oracle Pl/SQL</p>
            <p>MySQL</p>
            <p>PostScript</p>
            <p>Vue.js</p>
            <p>Next.js</p>
            <p>Python Num.py</p>
            <li>学んできたサーバー</li>
            <p><br />AWS</p>
            <p>Linux Gentoo</p>
            <p>Linux Arch</p>
            <p>Linux Cent OS</p>
            <p>Linux Ubuntu</p>
            <p>Windows Server</p>
          </ul>
          -->
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
