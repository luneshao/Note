# elementUI

## 1.select 同时获取value和label

[原文链接](http://www.manongjc.com/article/7713.html)

```html
<el-form-item label="库位" prop="goodsLocationId" >
  <el-col :span="15">
    <el-select v-model="scope.row.goodsLocationId" placeholder="货位地址" @change="changeLocationValue">
     <el-option v-for="lo in locations" :label="lo.locationName" :value="lo.id" :key="lo.id"></el-option>
    </el-select>
  </el-col>
</el-form-item>
```
```javascript
changeLocationValue(val){
  //locations是v-for里面的也是datas里面的值
  let obj = {};
  obj = this.locations.find((item)=>{
    return item.id === val;
  });
  this.wareHouseVO2.goodsLocationName = obj.locationName;
}
```
