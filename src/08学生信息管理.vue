<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model.number="age" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="addFn">添加/修改</button>
    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="(item, index) in list" :key="item.id">
          <td>{{ index + 1 }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="del(item.id)">删除</button>
            <button @click="edit(item.id)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  name: 'App',
  data() {
    return {
      flag: 0,
      name: '',
      age: '',
      sex: '男',
      list: [
        { id: 1, name: 'Tom', age: 20, sex: '男' },
        { id: 2, name: 'Jone', age: 22, sex: '男' },
        { id: 3, name: '小李', age: 19, sex: '女' },
        
      ],
    }
  },
  methods: {
    addFn() {
      if (!this.flag) {
        // 添加
        if (this.name == '' || this.age == '') return alert('请输入完整')
        this.list.push({
          id: this.list.length ? this.list[this.list.length - 1].id + 1 : 1,
          name: this.name,
          age: this.age,
          sex: this.sex,
        })
        this.name = ''
        this.age = ''
        this.sex = '男'
        return
      }
      // 修改
      const index = this.list.findIndex((item) => item.id == this.flag)
      this.$set(this.list, index, {
        id: this.flag,
        name: this.name,
        age: this.age,
        sex: this.sex,
      })
      this.flag = 0
      this.name = ''
      this.age = ''
      this.sex = '男'
    },
    del(id) {
      const index = this.list.findIndex((item) => item.id == id)
      this.list.splice(index, 1)
    },
    edit(id) {
      const item = this.list.filter((item) => item.id == id)
      this.name = item[0].name
      this.age = item[0].age
      this.sex = item[0].sex
      this.flag = id
    },
  },
}
</script>
