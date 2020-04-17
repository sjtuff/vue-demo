<template>
  <div>
    <Form ref="dictionaryForm" :model="helloWorldData" :label-width="100">
      <Row>
        <i-col span="5">
          <FormItem label="姓名" prop="name">
            <i-input clearable v-model="helloWorldData.name"></i-input>
          </FormItem>
        </i-col>
        <i-col span="5">
          <FormItem label="邮箱" prop="email">
            <i-input clearable v-model="helloWorldData.email"></i-input>
          </FormItem>
        </i-col>
      </Row>
      <Row>
        <i-col span="5">
          <Button type="primary" @click="save">保存</Button>
        </i-col>
      </Row>
    </Form>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App',
        helloWorldData: {
          name: '',
          email:''
        }
      }
    },
    methods:{
      save(){
        this.$api.post('saveUser', JSON.stringify(this.helloWorldData), response => {
          console.log("====response:",JSON.stringify(response))
        });
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
