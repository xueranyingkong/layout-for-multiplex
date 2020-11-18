<template>
  <div class="container">
    <el-upload :limit="limit" :action="uploadUrl" list-type="picture-card" :on-preview="handlePictureCardPreview" :on-remove="handleRemove" :on-success="handleListSuccess" :file-list="fileList" :data="data">
      <i class="el-icon-plus" />
    </el-upload>
    <el-dialog :visible.sync="dialogVisible">
      <img width="100%" :src="dialogImageUrl" alt="">
    </el-dialog>
  </div>
</template>

<script>
export default {
  props: {
    limit: {
      type: Number,
      default: 1
    }
  },
  data() {
    return {
      dialogImageUrl: '',
      dialogVisible: false,
      uploadUrl: 'https://dev-cloud-services.haier-ioc.com/cloudApi/datacenter/file/uploadFile',
      data: {
        useDay: 1,
        path: 'three-wings-bird/activity',
        projectId: 4
      },
      fileList: [],
      pathList: [],
      allUrlString: '',
      imgIp: this.proce
    }
  },
  methods: {
    handleRemove(file, fileList) {
      // 重置预览数据
      this.fileList = fileList
      // 删除路径数组内对应的元素
      for (const index in this.pathList) {
        if (`${process.env.VUE_APP_FILE_URL}/${this.pathList[index]}` === file.url) {
          this.pathList.splice(index, 1)
        }
      }
      // 重置路径合集字符串
      this.allUrlString = this.pathList.join(',')
      const data = {
        fileLsit: this.fileList,
        pathList: this.pathList,
        allUrlString: this.allUrlString
      }
      this.$emit('upload_over', data)
      console.log('删除', this.fileList, this.pathList, this.allUrlString)
    },
    handlePictureCardPreview(file) {
      this.dialogImageUrl = file.url
      this.dialogVisible = true
    },
    handleListSuccess(res, file) {
      if (res.code === 200) {
        const obj = {
          name: '图片',
          url: res.data.ip + '/' + res.data.fileUrl
        }
        // 添加入预览数组
        this.fileList.push(obj)
        // 添加入路径数组
        this.pathList.push(res.data.fileUrl)
        // 路径合集字符串用逗号隔开
        this.allUrlString = this.pathList.join(',')
        const data = {
          fileLsit: this.fileList,
          pathList: this.pathList,
          allUrlString: this.allUrlString
        }
        this.$emit('upload_over', data)
        console.log('新增', this.fileList, this.pathList, this.allUrlString)
      } else {
        this.$message.error('上传图片失败')
      }
    }
  }
}
</script>
