<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="StudentName" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model.number="StudentAge" />
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
        <tr v-for="item in list" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
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
        { id: 1, name: 'Tom', age: 19, sex: '男' },
        { id: 2, name: 'Jone', age: 21, sex: '女' },
        { id: 3, name: '小李', age: 18, sex: '男' },
      ],
      StudentName: '',
      StudentAge: '',
      sex: [],
      flag: false,
      id: '',
    }
  },

  methods: {
    addFn() {
      if (this.flag) {
        this.list[this.id] = {
          id: this.id,
          name: this.StudentName,
          age: this.StudentAge,
          sex: this.sex,
        }
      } else {
        this.list.push({
          id: this?.list[this.list.length - 1]?.id + 1 || 1,
          name: this.StudentName,
          age: this.StudentAge,
          sex: this.sex,
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
      this.sex = this.list[index].sex
      this.flag = true
      this.id = index
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
