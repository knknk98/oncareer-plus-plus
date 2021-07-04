<template>
      <v-card class="my-10" >
        <v-card-text>
          <div class="flex-row d-flex">
            <div>
              <User />
            </div>
            <div class="attr_box d-flex flex-column align-self-center">
              <div class="user_attr">{{userAttr}}</div>
              <div class="industry">{{afterJobType}}</div>
            </div>
          </div>
          <v-simple-table v-if="isDetail" class="job_type_table">
            <tbody>
            <tr>
              <td class="job_type_title">退社時の職種</td>
              <td >{{beforeJobType}}</td>
            </tr>
            <tr>
              <td class="job_type_title">入社時の職種</td>
              <td>{{afterJobType}}</td>
            </tr>
            </tbody>
          </v-simple-table>
          <div class="flex-row d-flex flow">
            <img class="arrow" src="@/assets/img/arrow.png"/>
            <div class="attr_box d-flex flex-column justify-space-between">
              <div class="d-flex">
                <NoImage />
                <div class="attr_box d-flex flex-column align-self-center">
                  <div class="user_attr comp_name">{{beforeCompName}}</div>
                  <div class="industry_arrow">{{beforeJobType}}</div>
                </div>
              </div>
              <div class="d-flex">
                <NoImage />
                <div class="attr_box d-flex flex-column align-self-center ">
                  <div class="user_attr comp_name">{{afterCompName}}</div>
                  <div class="industry_arrow">{{afterJobType}}</div>
                </div>
              </div>
            </div>
          </div>
          <section class="content_section">
            <h2 class="content_title">このキャリアを選んだ理由</h2>
            <p :class="{'content':isDetail === false}">
              {{content1}}
            </p>
            <NuxtLink v-if="isDetail==false" to="/details">もっと見る</NuxtLink>
          </section>
          <section class="content_section">
            <h2 class="content_title">重視したポイント</h2>
            <p :class="{'content':isDetail === false}">
              {{content2}}
            </p>
            <NuxtLink v-if="isDetail==false" to="/details">もっと見る</NuxtLink>
          </section>
          <section class="content_section">
            <h2 class="content_title">他に検討したキャリア</h2>
            <p :class="{'content':isDetail === false}">
              {{content3}}
            </p>
            <NuxtLink v-if="isDetail==false" to="/details">もっと見る</NuxtLink>
          </section>
          <hr class="my-3">
        </v-card-text>
        <v-card-actions v-if="isDetail">
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/"
          >
            戻る
          </v-btn>
        </v-card-actions>
      </v-card>
</template>

<script lang="ts">
import Vue from 'vue'
const DUMMY_CONTENTS1: String = "4年目の初めに全社営業表彰を獲得したタイミングで、将来のキャリアに不安を覚えて転職を志しました。グロービスに通学し、このまま人材派遣営業を続けていては、キャリア選択の幅が狭くなる事を確信して転職活動を始めました"
const DUMMY_CONTENTS2: String = "法人営業であり、これまでの経験が活かせることに加えて、経営者に対しての提案、ITリテラシー、金融リテラシーが身につく、大手ではなくこれから伸びていく会社、という事を重視しました"
const DUMMY_CONTENTS3: String = "フェイスブック：SNSでリクルーターから声がけがあり面談。当時はインスタグラムがまさに伸びている時期であり、ある程度将来性を感じていたが、Webサービスなのでプラットフォーマーに一つ劣るところだけが気になっていた。社長面接まで行なったが、別の候補者に内定が出たため最終選考で落選。"

export default Vue.extend({
  props: {
    isDetail: {
      type: Boolean,
      default:true,
    },
    userAttr: {
      type: String,
      default: "社会人５〜１０年 | 男性",
    },
    beforeJobType: {
      type: String,
      default: "法人営業",
    },
    afterJobType: {
      type: String,
      default: "法人営業",
    },
    beforeCompName: {
      type: String,
      default: "リクルートスタッフィング",
    },
    afterCompName: {
      type: String,
      default: "FUNDBOOK",
    },
    content1: {
      type: String,
      default: DUMMY_CONTENTS1,
    },
    content2: {
      type: String,
      default: DUMMY_CONTENTS2,
    },
    content3: {
      type: String,
      default: DUMMY_CONTENTS3,
    },

  }
})
</script>

<style>

.card_title{
  font-size:32px;
  font-weight:700;
  line-height:1.5;
  margin:32px 0;
}

.attr_box{
  margin-left:8px;
}
.user_attr{
  font-size:16px;
  font-weight: 700;
}
.industry{
  font-size:20px;
  font-weight: 700;
}
.industry_arrow{
  font-size:16px;
  font-weight: 700;
}
.comp_name{
  font-size:20px;
}
.job_type_table{
  text-align:left;
  margin-top :24px ;
}
.job_type_title{
  font-size:14px;
}
.arrow{
  display:block;
  height:150px;
}
.flow{
  margin : 50px 0;
}
.content_title{
  font-size:24px;
  margin:20px 0;
}
.content_section{
  margin: 40px 0;
}

.content {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  overflow: hidden;
  word-break: break-all;;  
}
</style>