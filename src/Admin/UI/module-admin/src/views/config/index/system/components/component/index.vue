<template>
  <nm-form-page v-bind="form" @success="onSuccess">
    <el-divider content-position="left">菜单</el-divider>
    <el-row :gutter="20">
      <el-col :span="10" :offset="1">
        <el-form-item label="保持一个子菜单的展开：" prop="menu.uniqueOpened">
          <el-switch v-model="form.model.menu.uniqueOpened" />
        </el-form-item>
      </el-col>
    </el-row>
    <el-divider content-position="left">对话框</el-divider>
    <el-row :gutter="20">
      <el-col :span="10" :offset="1">
        <el-form-item label="可点击模态框关闭：" prop="dialog.closeOnClickModal">
          <el-switch v-model="form.model.dialog.closeOnClickModal" />
        </el-form-item>
      </el-col>
      <el-col :span="10">
        <el-form-item label="默认可拖拽：" prop="dialog.draggable">
          <el-switch v-model="form.model.dialog.draggable" />
        </el-form-item>
      </el-col>
    </el-row>
    <el-divider content-position="left">列表页</el-divider>
    <el-row :gutter="20">
      <el-col :span="10" :offset="1">
        <el-form-item label="序号表头名称：" prop="list.serialNumberName">
          <el-input v-model="form.model.list.serialNumberName" placeholder="默认 #" />
        </el-form-item>
      </el-col>
    </el-row>
    <el-divider content-position="left">标签导航</el-divider>
    <el-row :gutter="20">
      <el-col :span="10" :offset="1">
        <el-form-item label="显示图标：" prop="tabnav.showIcon">
          <el-switch v-model="form.model.tabnav.showIcon" />
        </el-form-item>
      </el-col>
      <el-col :span="10">
        <el-form-item label="最大页面数量：" prop="tabnav.maxOpenCount">
          <el-input v-model.number="form.model.tabnav.maxOpenCount" placeholder="默认 20" />
        </el-form-item>
      </el-col>
    </el-row>
    <el-divider content-position="left">自定义CSS</el-divider>
    <el-row :gutter="20">
      <el-col :span="22" :offset="1">
        <el-form-item labelWidth="0" prop="customCss">
          <el-input type="textarea" :rows="5" placeholder="如果需要重新某个组件的样式，可以在此处添加覆盖的CSS" v-model="form.model.customCss"></el-input>
        </el-form-item>
      </el-col>
    </el-row>
  </nm-form-page>
</template>
<script>
import { mapMutations } from 'vuex'
const api = $api.admin.system
export default {
  data() {
    return {
      form: {
        header: false,
        action: api.updateComponentConfig,
        model: this.model,
        labelWidth: '200px'
      }
    }
  },
  props: {
    model: Object
  },
  methods: {
    ...mapMutations('app/system', ['setComponentConfig']),
    onSuccess() {
      this.setComponentConfig(this.form.model)
    }
  }
}
</script>
