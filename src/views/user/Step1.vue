<template>
  <div>
    <a-form :form="form" style="max-width: 500px; margin: 40px auto 0;">
      <a-form-item
        label="手机号"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
      >
        <a-input-group
          style="display: inline-block; vertical-align: middle"
          :compact="true"
        >
          <a-select defaultValue="alipay" style="width: 140px">
            <a-select-option value="alipay">中国大陆 +98</a-select-option>
            <a-select-option value="wexinpay">中国大陆 +98</a-select-option>
          </a-select>
          <a-input
            :style="{width: 'calc(100% - 140px)'}"
            v-decorator="['payType', { initialValue: '', rules: [{required: true, message: '必须填写手机号码'}]}]"
          />
        </a-input-group>
      </a-form-item>
      <a-form-item
        label="验证码"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
      >
        <a-input-group
          style="display: inline-block; vertical-align: middle"
          :compact="true"
        >
          <a-input style="width: 200px" v-decorator="['momey', { initialValue: '', rules: [{required: true, message: '必须填写验证码'}] }]"/>
          <a-button type="primary" :style="{width: 'calc(100% - 200px)'}">发送验证码</a-button>
        </a-input-group>
      </a-form-item>
      <a-form-item>
        <a-alert
          message="校验码已发送到你的手机，请查收！ 15分钟内输入有效，请勿泄露！"
          banner
          closable
        />
      </a-form-item>
      <a-form-item :wrapperCol="{span: 24}" :style="{textAlign: 'center'}">
        <a-button type="primary" @click="nextStep" :style="{paddingLeft: '40px',paddingRight:'40px'}">下一步</a-button>
      </a-form-item>
    </a-form>
    <a-divider />
    <div style="text-align: right"><router-link class="login" :to="{ name: 'login' }">使用已有账户登录</router-link></div>
  </div>
</template>

<script>
export default {
  name: 'Step1',
  data () {
    return {
      labelCol: { lg: { span: 5 }, sm: { span: 5 } },
      wrapperCol: { lg: { span: 19 }, sm: { span: 19 } },
      form: this.$form.createForm(this)
    }
  },
  methods: {
    nextStep () {
      const { form: { validateFields } } = this
      // 先校验，通过表单校验后，才进入下一步
      validateFields((err, values) => {
        if (!err) {
          this.$emit('nextStep')
        }
      })
    }
  }
}
</script>

<style lang="less" scoped>

</style>
