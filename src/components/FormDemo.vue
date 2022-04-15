// form.vue 
<template>
  <ElForm class="flex flex-column" label-width="180px">
    <FormProvider :form="form">
      <SchemaField
        :schema="schema"
      />
      <FormConsumer>
      <!-- 非常重要！！！！ FormConsumer必须是这个位置 才能表单消费 //官方文档根本不管VUE的死活在这里！！！-->
        <template #default="{ form }">
            <button @click='form.submit'>123</button>
        </template>
      </FormConsumer>
    </FormProvider>
  </ElForm>
</template>

<script>
import { createForm, onFormValuesChange, onFormSubmit } from '@formily/core' //必须要引入
import { FormProvider, createSchemaField, FormConsumer } from '@formily/vue' //vue
import { Input } from 'element-ui' //初次上手建议 就直接引用element UI 组件就可以了

const { SchemaField } = createSchemaField({
  Input
}) //代表你需要这个生成器给你生成什么样的表单组件

export default {
    components: { FormProvider, SchemaField, FormConsumer },
    data() {
        return {
            form: createForm({effects: this.useEffects}), //生成表单的方法，传入监听的参数
            schema: null
        }
    },
    mounted() {
        this.schema = {
            type: 'object',
            properties: {
              name: {
                type: 'string',
                title: '名称',
                required: true,
                'x-component': 'Input'
              }
            }
        }
    },
    methods: {
        useEffects() {
          onFormValuesChange(form => { //监听数据变化了
            console.log(form) //这个form 很重要 这里你才能够拿到表单的值
          })
          onFormSubmit(form => { //监听表单提交
            console.log(form)
          })
        },
    }
}
</script>