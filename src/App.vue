<template>
  <div id="app">
    <h1>TODOアプリ</h1>
    <div>
      <label for="title">タスク名：</label>
      <input type="text" v-model="title" placeholder="">
      <label for="body">推定時間（分）：</label>
      <input type="text" v-model="body" placeholder="">
    </div>
    <div>
      <input type="submit" value="追加" @click="addList">
    </div>
    <ul>
      <li> タスク　　　推定時間（分）
      </li>
    </ul>
    <ul v-for="(list, i) in lists" v-bind:key="i">
      <li> {{ list.title }}　　　　{{ list.body }} 
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  data: () => ({
    lists: [
      {title: '予習', body: '30分'},
      {title: '学習', body: '40分'}
    ],
    title: '',
    body: ''
  }),
  methods: {
    // リストの追加
    addList: function(){
      if(this.title === '' || this.body === '') return

      this.lists.push({title: this.title, body: this.body})
      this.title = ''
      this.body = ''
    },
    // リストの削除
    deleteList: function(i){
      this.lists.splice(i,1)
    }
  }
};
</script>
