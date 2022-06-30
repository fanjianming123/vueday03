<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="newObj.name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model.number="newObj.age" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="newObj.sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="addOrEditFn">添加/修改</button>
    </div>
    <div>
      <table
        border="1"
        cellpadding="10"
        cellspacing="0"
        v-show="dataArr.length > 0"
      >
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="(obj, index) in dataArr" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ obj.name }}</td>
          <td>{{ obj.aeg }}</td>
          <td>{{ obj.sex }}</td>
          <td>
            <button @click="del(index)">删除</button>
            <button @click="edit(index)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newObj: {
        name: '',
        age: 0,
        sex: '',
      },
      editIndex: null, // 保存正在编辑的对象的索引，注意这里的初始值不能为0及0以上的数
      dataArr: [
        {
          name: 'zs',
          age: 18,
          sex: '男',
        },
        {
          name: 'Jone',
          age: 21,
          sex: '女',
        },
      ],
    }
  },
  methods: {
    // 添加/修改 点击事件的方法
    addOrEditFn() {
      // 注意：对象是引用关系，所以必须让数组里的对象和newObj脱离引用关系，因为这里只有一层，于是我们可以利用浅拷贝实现
      let theObj = { ...this.newObj }

      if (this.editIndex !== null) {
        this.$set(this.dataArr, this.editIndex, theObj)

        this.editIndex = null // 更新后，保证下次点击是新增效果
      } else {
        // 新增
        this.dataArr.push(theObj)
      }
    },
    // 实现删除功能
    del(index) {
      this.dataArr.splice(index, 1)
    },
    // 实现编辑功能
    edit(index) {
      // 取出要编辑的对象信息
      const editObj = this.dataArr[index]
      this.username = editObj.name
      this.userage = editObj.age
      this.gender = editObj.sex
      //优化
      // this.newObj = { ...editObj }

      this.editIndex = index // 保存当前的索引值
    },
  },
}
</script>
