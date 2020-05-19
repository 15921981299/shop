<template>
  <div>
    <a-form :form="form" style="max-width: 500px; margin: 40px auto 0;">
      <a-form-item
        label="登录名"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
        class="stepFormText"
      >
        15965456455
      </a-form-item>
      <a-divider />
      <a-form-item
        label="请设置登录密码"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
        class="stepFormText"
      >
        登录时验证，保护账号信息
      </a-form-item>
      <a-form-item
        label="登录密码"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
        class="stepFormText"
      >
        <a-input v-decorator="['momey', { initialValue: '', rules: [{required: true, message: '必须填写登录密码'}] }]"/>
      </a-form-item>
      <a-form-item
        label="确认密码"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
        class="stepFormText"
      >
        <a-input v-decorator="['momey', { initialValue: '', rules: [{required: true, message: '必须填写确认密码'}] }]"/>
      </a-form-item>
      <a-divider />
      <a-form-item
        label="设置会员昵称"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
        class="stepFormText"
      >
        会员昵称一旦设置成功，无法修改
      </a-form-item>
      <a-form-item
        label="会员昵称"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
        class="stepFormText"
      >
        <a-input v-decorator="['momey', { initialValue: '', rules: [{required: true, message: '必须填写会员昵称'}] }]"/>
      </a-form-item>
      <a-form-item :wrapperCol="{span: 24}" :style="{textAlign: 'center'}">
        <a-button  @click="prevStep" :style="{paddingLeft: '40px',paddingRight:'40px',marginRight:'16px'}">上一步</a-button>
        <a-button :loading="loading" type="primary" @click="nextStep" :style="{paddingLeft: '40px',paddingRight:'40px'}">提交</a-button>
      </a-form-item>
    </a-form>
    <a-divider />
    <div style="text-align: right"><router-link class="login" :to="{ name: 'login' }">使用已有账户登录</router-link></div>
  </div>
</template>

<script>
export default {
  name: 'Step2',
  data () {
    return {
      labelCol: { lg: { span: 5 }, sm: { span: 5 } },
      wrapperCol: { lg: { span: 19 }, sm: { span: 19 } },
      form: this.$form.createForm(this),
      loading: false,
      timer: 0
    }
  },
  methods: {
    nextStep () {
      const that = this
      const { form: { validateFields } } = this
      that.loading = true
      validateFields((err, values) => {
        if (!err) {
          console.log('表单 values', values)
          that.timer = setTimeout(function () {
            that.loading = false
            that.$emit('nextStep')
          }, 1500)
        } else {
          that.loading = false
        }
      })
    },
    prevStep () {
      this.$emit('prevStep')
    }
  },
  beforeDestroy () {
    clearTimeout(this.timer)
  }
}
</script>

<style lang="less" scoped>
  .stepFormText {
    margin-bottom: 24px;

    .ant-form-item-label,
    .ant-form-item-control {
      line-height: 22px;
    }
  }

</style>
