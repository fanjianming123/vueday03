<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="StudentName" placeholder="请输入姓名" />
    </div>
    <div>
      <span>年龄:</span>
      <input
        type="number"
        v-model.number="StudentAge"
        placeholder="请输入年龄"
      />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="gender">
        <option :value="1">男</option>
        <option :value="0">女</option>
      </select>
    </div>
    <div>
      <button @click="addFn">{{flag?'修改':'添加'}}</button>
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
        <tr v-for="item in list" :key="item.id">
          <td>{{ item.id}}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ ['女', '男'][item.sex] }}</td>
          <td>
            <button @click.prevent="del(item.id)">删除</button>
            <button @click.prevent="edit(item.id)">编辑</button>
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
      list: [
        { id: 1, name: 'Tom', age: 19, sex: 1 },
        { id: 2, name: 'Jone', age: 21, sex: 0 },
        { id: 3, name: '小李', age: 18, sex: 1 },
      ],
      StudentName: '',
      StudentAge: '',
      gender: '',
      flag: false,
      currentId: '',
    }
  },

  methods: {
    addFn() {
      if (
        this.StudentName === '' ||
        this.StudentAge === '' ||
        this.gender === ''
      ) {
        return alert('please enter')
      }
      if (this.flag) {
        this.list[this.currentId] = {
          id: this.list[this.currentId].id,
          name: this.StudentName,
          age: this.StudentAge,
          sex: this.gender,
        }
        this.flag = false
      } else {
        this.list.push({
          id: this?.list[this.list.length - 1]?.id + 1 || 1,
          name: this.StudentName,
          age: this.StudentAge,
          sex: this.gender,
        })
      }

      this.StudentName = ''
      this.StudentAge = ''
      this.sex = ''
    },
    del(id) {
      this.list = this.list.filter((item) => item.id !== id)
    },
    edit(id) {
      const index = this.list.findIndex((item) => item.id === id)
      this.StudentName = this.list[index].name
      this.StudentAge = this.list[index].age
      this.gender = this.list[index].sex
      this.flag = true
      this.currentId = index
    },
  },
}
</script>

<style scoped>
table {
  border-collapse: collapse;
}
td,
th {
  border: 1px solid #333;
}
</style>
