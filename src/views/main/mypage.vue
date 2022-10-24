<template>
  <div class="MyPage">
    <h3><b-icon icon="person" scale="0.9"></b-icon> My Page</h3>
    <b-card title="회원정보" class="mpcard">
      <!-- <b-form @submit="onSubmit" @reset="onReset"> -->
      <b-row class="my-1">
        <b-col sm="3">
          <label for="id">아이디:</label>
        </b-col>
        <b-col sm="6">
          <p>{{ user.userId }}</p>
        </b-col>
      </b-row>
      <b-row class="my-1">
        <b-col sm="3">
          <label>이름:</label>
        </b-col>
        <b-col sm="6">
          <p>{{ user.name }}</p>
        </b-col>
      </b-row>
      <b-row class="my-1">
        <b-col sm="3">
          <label for="phone">폰번호:</label>
        </b-col>
        <b-col sm="6">
          <p v-if="show" id="phone">
            {{ user.ownerPhone }}
            <button v-if="show" class="PhoneB" variant="outline-primary" @click="show = !show">
              <b-icon icon="pencil" class="pencil"></b-icon>
            </button>
          </p>
          <div class="PHONEB">
            <b-input v-if="!show" v-model="ownerPhone"></b-input>
            <b-btn v-if="!show" variant="danger" @click="show = !show">취소</b-btn>
          </div>
        </b-col>
      </b-row>
      <b-row class="my-1">
        <b-col sm="3">
          <label for="email">이메일:</label>
        </b-col>
        <b-col sm="6">
          <p id="email">{{ user.email }}</p>
        </b-col>
      </b-row>
      <b-row class="my-1">
        <b-col sm="3">
          <label for="password">비밀번호:</label>
        </b-col>
        <b-col sm="7">
          <b-input
            v-if="!on"
            v-model="currentPassword"
            placeholder="현재 비밀번호를 입력하세요."
            type="password"
          ></b-input>
          <b-input v-if="!on" v-model="newPassword" placeholder="새 비밀번호를 입력하세요." type="password"></b-input>
          <button v-if="on" class="PhoneB" variant="outline-primary" @click="on = !on">
            <b-icon icon="pencil" class="pencil"></b-icon>
          </button>
          <b-btn v-if="!on" variant="danger" @click="on = !on">취소</b-btn>
        </b-col>
      </b-row>
      <b-row class="my-1">
        <b-col sm="10">
          <b-btn class="Save" variant="success" @click="updateprofile">저장</b-btn>
        </b-col>
      </b-row>
    </b-card>
    <div class="TTT" style="cursor: pointer" @click="$bvModal.show('modal-member-TTT')">탈퇴하기</div>
    <b-modal id="modal-member-TTT" title="계정삭제" style="text-align: center" hide-footer>
      <b-form-group style="text-align: center">
        <img class="IMOGG" src="../../../public/sad.png" />
        <p>정말로 탈퇴하시겠습니까?<br />가입한 멤버쉽 정보를 살펴보신 후 눌러주세요.</p>
        <b-btn variant="danger" @click="deleteprofile">탈퇴하기</b-btn>
      </b-form-group>
    </b-modal>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data: () => ({
    user: {},
    ownerPhone: '',
    currentPassword: '',
    newPassword: '',
    password: '',
    show: true,
    on: true
  }),
  mounted() {
    this.inforData()
  },
  methods: {
    async inforData() {
      await axios
        .get(process.env.VUE_APP_URL + '/profile/info', {
          headers: {
            Authorization: `Bearer ${localStorage.getItem('token')}`
          }
        })
        .then(async res => {
          this.user = res.data.data
          console.log('inforData - response: ', res.data.data)
        })
        .catch(err => {
          console.log('inforData - error: ', err)
        })
    },
    async updateprofile() {
      const axiosBody = {
        currentPassword: this.currentPassword,
        newPassword: this.newPassword,
        ownerPhone: this.ownerPhone
      }
      console.log('updateprofile - axiosBody', axiosBody)

      await axios
        .put(process.env.VUE_APP_URL + '/profile/update-profile', axiosBody, {
          headers: {
            Authorization: `Bearer ${localStorage.getItem('token')}`
          }
        })
        .then(response => {
          console.log('updateprofile - response : ', response)
          alert('회원정보가 수정 되었습니다.')
          this.$router.go()
        })
        .catch(error => {
          console.log('updateprofile - error : ', error)
        })
    },
    async deleteprofile() {
      // console.log('되나?', this.user.password)
      await axios
        .delete(process.env.VUE_APP_URL + '/profile/remove-profile/' + this.user.email, {
          headers: {
            Authorization: `Bearer ${localStorage.getItem('token')}`
          }
        })
        .then(response => {
          console.log('deleteprofile - response : ', response)
          alert('탈퇴 되었습니다. 마이 스탬프는 점주님을 다시 만나길 진심으로 바라고 있습니다.')
          localStorage.removeItem('token')
          this.$router.push('/')
        })
        .catch(error => {
          console.log('deleteprofile - error : ', error)
        })
    }
  }
}
</script>
<style>
.Mfooter {
  /* margin-top: 161px; */
  font-size: 12px;
  color: #fff;
  background: #5a38d4;
  letter-spacing: 2px;
  padding: 2vh 5vw;
  display: flex;
  justify-content: center;
}
.MyPage {
  width: 100%;
  height: 100vh;
  padding: 25px;
}
.mpcard {
  width: 50%;
  height: 65vh;
  padding: 25px;
  margin-top: 20px;
  margin-left: 22vw;
  border: none;
  border-radius: 15px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1), 0 3px 6px rgba(0, 0, 0, 0.1);
}
.pencil {
  transition: 0.5s;
}
.PhoneB {
  width: 35px;
  height: 35px;
  background-color: #fff;
  border-radius: 20px;
  border: none;
  transition: 0.5s;
}
.PhoneB:hover {
  background-color: #432a9f;
}
.PhoneB:hover .pencil {
  color: #fff;
}
.PHONEB {
  display: grid;
  grid-template-columns: 4fr 2fr;
}
.TTT {
  text-align: center;
  padding-top: 15px;
  padding-left: 40%;
  color: red;
}
.IMOGG {
  width: 100px;
  margin-bottom: 15px;
}
</style>
