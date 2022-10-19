<template>
  <div class="fnqContainer">
    <div class="job-wrap">
      <div class="job-image">
        <img src="../../public/job.jpg" />
        <div class="job-text">
          <p>자주묻는 질문과 답변</p>
          <span>FAQ</span>
        </div>
      </div>
      <div class="job-text">
        <p>자주묻는 질문과 답변</p>
        <span>FAQ</span>
      </div>
      <div class="faqList">
        <div v-for="(list, i) in faqList" :key="list" :faqList="faqList[i]" class="faq">
          <div class="faqHeading">
            <p>{{ faqList[i].category }}</p>
            <p>{{ faqList[i].title }}</p>
          </div>
          <div class="faqBody">
            <p>{{ faqList[i].comment }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FAQ from '@/assets/FAQ.js'

export default {
  data() {
    return {
      faqList: FAQ
    }
  }
}
</script>

<style>
.job-wrap {
  width: 100%;
  margin: 10px auto;
  position: relative;
}
.job-wrap img {
  width: 100%;
  height: 55vh;
  object-fit: cover;
  filter: brightness(60%);
}
.job-text {
  position: absolute;
  top: 47%;
  left: 50%;
  width: 100%;
  transform: translate(-50%, -50%);
  font-size: 3vw;
  font-weight: bold;
  text-align: center;
  color: #fff;
}
.fnqContainer {
  display: grid;
  grid-template-rows: 10% 90%;
}
.faqList {
  display: grid;
  grid-template-rows: 30% 70%;
  margin: 50px;
}
.faqHeading {
  display: grid;
  grid-template-columns: 15% 85%;
}
/* .faqBody {} */
.faq {
  width: 80%;
}
</style>
