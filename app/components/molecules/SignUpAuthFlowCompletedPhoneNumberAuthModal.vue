<template>
  <div>
    <div class="modal-body">
      <p class="announce">
        ALISへようこそ
      </p>
      <p class="description">
        ALISトークンを報酬として受け取ることができるようになりました。ALIS
        で多くの人や信頼できる人から支持される記事を書くか、信頼できる記事
        をいち早くみつけるほど多くのALISトークンが配布されます。
      </p>
      <img
        class="completed-auth-img"
        src="~/assets/images/pc/common/image_certification.jpg"
        alt="completed-auth-image">
    </div>
    <div class="modal-footer">
      <!-- <app-button class="to-next-step-button" @click="transitToProfileSettings">
        プロフィールを作成する
      </app-button> -->
      <button class="to-top-button" @click="transitToTop">
        TOPに戻る
      </button>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
// import AppButton from '../atoms/AppButton'

export default {
  components: {
    // AppButton
  },
  methods: {
    transitToProfileSettings() {
      this.setSignUpAuthFlowCompletedPhoneNumberAuthModal({
        isSignUpAuthFlowCompletedPhoneNumberAuthModal: false
      })
      this.setSignUpAuthFlowProfileSettingsModal({
        isSignUpAuthFlowProfileSettingsModal: true
      })
    },
    transitToTop() {
      document.querySelector('html,body').style.overflow = ''
      this.setSignUpAuthFlowModal({
        showSignUpAuthFlowModal: false
      })
    },
    ...mapActions('user', [
      'setSignUpAuthFlowModal',
      'setSignUpAuthFlowCompletedPhoneNumberAuthModal',
      'setSignUpAuthFlowProfileSettingsModal'
    ])
  }
}
</script>

<style lang="scss" scoped>
.modal-body {
  margin: 0 auto;

  .announce {
    @include default-text();
    font-size: 14px;
    margin: 60px 0 0;
    text-align: center;
  }

  .description {
    @include default-text();
    margin: 20px auto 0;
    max-width: 400px;
  }

  .completed-auth-img {
    width: 280px;
    margin: 24px auto 0;
    display: block;
  }
}

.modal-footer {
  width: 270px;
  margin: 40px auto 40px;

  .to-next-step-button {
    margin: 20px auto 0;
  }

  .to-top-button {
    background: #fff;
    border-radius: 18px;
    border: 1px solid #858dda;
    color: #858dda;
    cursor: pointer;
    display: block;
    font-size: 14px;
    margin: 20px auto 0;
    outline: none;
    padding: 10px;
    text-align: center;
    text-decoration: none;
    width: 265px;

    &:focus {
      opacity: 0.8;
    }

    &:target {
      display: block;
    }
  }
}
</style>
