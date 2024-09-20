# mall-admin-web

## 添加商品属性及 locale 处理 

- 首页/商品/修改商品
  - 填写商品属性
    - 属性类型 
      目前只支持中文
    - 商品规格 项
      添加 locale 支持即 增加 locale 为 En 的属性描述
      ![alt text](image.png)
    - sku 项修改
      ![alt text](image-1.png)
    - 商品参数项修改
      ![alt text](image-2.png)    
    - 商品详情
      增加 电脑端详情  locale == en 部分 
      增加 移动端详情  locale == en 部分
  - 商品信息  修改
    - 商品分类 ![alt text](image-3.png)
    - 商品品牌 ![alt text](image-4.png)  需要修改 
  - 商品促销
    - 优惠方式 ![alt text](image-5.png)  需要修改支持 locale == en 的情况


## 添加商品类型属性 及 locale 处理 

- 首页/商品/商品属性
  - 属性值可选值列表
    - 增加 locale == en 的 列表
    - ![alt text](image-6.png)
  - 商品属性列表
    - 增加 input_list_en 展示
    - ![alt text](image-7.png)
    - ![alt text](image-8.png)
  - 商品参数列表
    - ![alt text](image-9.png)

## 添加商品 Sku 相关编辑选项 （未添加）

- 增加 sku 页面
  - 列表 sku
  - 编辑 sku 库存/ 属性修改 

## 添加数据分析页面 （未添加）

- 增加 统计信息 页面
  - 编辑 sku 库存/ 属性修改 

## order Detail 页面修改 

- 商品信息项 
  - 增加 商品 name_en
  - 增加 属性 En  


## el-loader 添加 authorization

~~~html

    <el-upload
      :action="useOss?ossUploadUrl:minioUploadUrl"
      :data="useOss?dataObj:null"
      list-type="picture"
      :multiple="false" :show-file-list="showFileList"
      :file-list="fileList"
      :before-upload="beforeUpload"
      :on-remove="handleRemove"
      :on-success="handleUploadSuccess"
      :on-preview="handlePreview"
      :headers="customHeader" 
      >
      <el-button size="small" type="primary">点击上传</el-button>
      <div slot="tip" class="el-upload__tip">只能上传jpg/png文件，且不超过10MB</div>
    </el-upload>
  
<script>
  import {policy} from '@/api/oss'
  import { getToken } from '@/utils/auth'
  export default {
    name: 'singleUpload',
    props: {
      value: String
    },
    
    data() {
      return {
        dataObj: {
          policy: '',
          signature: '',
          key: '',
          ossaccessKeyId: '',
          dir: '',
          host: '',
          // callback:'',
          
        },
        customHeader: {
          Authorization: getToken()
        },
        dialogVisible: false,
        useOss:false, //使用oss->true;使用MinIO->false
        ossUploadUrl:'http://macro-oss.oss-cn-shenzhen.aliyuncs.com',
        minioUploadUrl:'http://localhost:8080/minio/upload',
        //minioUploadUrl:'http://192.168.2.119:8086/minio/upload',
      };
    }
  }
 </script>

~~~


## 输入值问题
需指定 input 的 model.number ，才能转化为 int 型 
![alt text](image-10.png)


## 日期选择器 

~~~html
<el-date-picker
  v-model="dateTime"
  type="datetime"
  placeholder="选择日期时间"
  value-format="yyyy-MM-dd'T'HH:mm:ss'Z'"
  format="yyyy-MM-dd HH:mm:ss">
</el-date-picker>

~~~

