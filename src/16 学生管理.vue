<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model="name" />
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
        <tr v-for="item in list" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="del(item.id)">删除</button>
            <button @click="editFn(item.id)">编辑</button>
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
      list: [
        { id: 1, name: 'Tom', age: 19, sex: '男' },
        { id: 2, name: 'Jone', age: 21, sex: '女' },
        { id: 3, name: '小李', age: 18, sex: '男' },
      ],
      name: '',
      age: 0,
      sex: '',
      flag: false,
      indexId: 0,
    };
  },
  methods: {
    addFn() {
      if (this.name === '' || this.age === 0 || this.sex === '')
        return alert('Please enter');
      if (!this.flag) {
        this.list.push({
          id: this.list[this.list.length - 1]?.id + 1 || 1,
          name: this.name,
          age: this.age,
          sex: this.sex,
        });
        this.name = '';
        this.age = '';
        this.sex = '';
        return;
      }
      const index = this.list.findIndex((ele) => ele.id == this.indexId);
      this.$set(this.list, index, {
        id: this.indexId,
        name: this.name,
        age: this.age,
        sex: this.sex,
      });

      this.flag = false;
      this.name = '';
      this.age = '';
      this.sex = '';
      this.indexId = 0;
    },
    editFn(val) {
      const index = this.list.findIndex((ele) => ele.id == val);
      this.name = this.list[index].name;
      this.age = this.list[index].age;
      this.sex = this.list[index].sex;
      this.flag = true;
      this.indexId = index;
    },
    del(val) {
      const index = this.list.findIndex((ele) => ele.id == val);
      this.list.splice(index, 1);
    },
  },
};
</script>
