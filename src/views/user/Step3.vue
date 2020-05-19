<template>
  <div>
    <a-form style="margin: 40px auto 0;">
      <result title="注册成功" :is-success="true" style="max-width: 560px;">
        <div class="information">
          <a-row>
            <a-col :sm="24" :xs="24" style="text-align: center">您的账户信息如下</a-col>
          </a-row>
          <a-divider />
          <a-row>
            <a-col :sm="8" :xs="24">登录名：</a-col>
            <a-col :sm="16" :xs="24">159216545699</a-col>
          </a-row>
          <a-row>
            <a-col :sm="8" :xs="24">绑定手机：</a-col>
            <a-col :sm="16" :xs="24">159216545699(用于接收短信校验码)</a-col>
          </a-row>
          <a-row>
            <a-col :sm="8" :xs="24">会员昵称：</a-col>
            <a-col :sm="16" :xs="24">恭喜发财</a-col>
          </a-row>
        </div>
        <div slot="action" :style="{textAlign: 'center'}">
          <router-link class="login" :to="{ name: 'login' }">
            <a-button type="primary" :style="{paddingLeft: '40px',paddingRight:'40px'}">立即登录</a-button>
          </router-link>
        </div>
      </result>
    </a-form>
  </div>
</template>

<script>
import { Result } from '@/components'

export default {
  name: 'Step3',
  components: {
    Result
  },
  data () {
    return {
      loading: false
    }
  },
  methods: {
    finish () {
      this.$emit('finish')
    },
    toOrderList () {
      this.$router.push('/list/table-list')
    }
  }
}
</script>
<style lang="less" scoped>
  .information {
    line-height: 22px;

    .ant-row:not(:last-child) {
      margin-bottom: 24px;
    }
  }
  .money {
    font-family: "Helvetica Neue",sans-serif;
    font-weight: 500;
    font-size: 20px;
    line-height: 14px;
  }
</style>
