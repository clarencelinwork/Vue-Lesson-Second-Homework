<script setup>
import { RouterLink } from 'vue-router'
import { ref, onMounted } from 'vue'

const currentType = ref('全部')
const newTodo = ref('')

const todoListData = ref([
  {
    id: _uuid(),
    name: '把冰箱發霉的檸檬拿去丟',
    status: true,
  },
  {
    id: _uuid(),
    name: '打電話叫媽媽匯款給我',
    status: true,
  },
  {
    id: _uuid(),
    name: '整理電腦資料夾',
    status: true,
  },
  {
    id: _uuid(),
    name: '繳電費水費瓦斯費',
    status: true,
  },
  {
    id: _uuid(),
    name: '約vicky禮拜三泡溫泉',
    status: true,
  },
  {
    id: _uuid(),
    name: '約ada禮拜四吃晚餐',
    status: true,
  },
])

const todoListCount = ref(0)
const todoListFinishCount = ref(0)
const todoListUnFinishCount = ref(0)

onMounted(() => {
  updateCount()
})

function updateCount() {
  todoListCount.value = todoListData.value.length
  todoListFinishCount.value = todoListData.value.filter((item) => item.status === true).length
  todoListUnFinishCount.value = todoListData.value.filter((item) => item.status === false).length
}

function removeItem(id) {
  todoListData.value = todoListData.value.filter((item) => item.id !== id)
  updateCount()
}

function changeType(type) {
  switch (type) {
    default:
    case '全部':
      currentType.value = '全部'
      break
    case '待完成':
      currentType.value = '待完成'
      break
    case '已完成':
      currentType.value = '已完成'
      break
  }
  updateCount()
}

function addTodo() {
  // 假設你新增一個項目
  const newTodoItem = { id: _uuid(), name: newTodo.value, status: false }
  // 使用 push() 方法將新項目加入陣列尾部
  todoListData.value.push(newTodoItem)
  newTodo.value = ''
  updateCount()
}

function _uuid() {
  let d = Date.now()
  if (typeof performance !== 'undefined' && typeof performance.now === 'function') {
    d += performance.now() //use high-precision timer if available
  }
  return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function (c) {
    const r = (d + Math.random() * 16) % 16 | 0
    d = Math.floor(d / 16)
    return (c === 'x' ? r : (r & 0x3) | 0x8).toString(16)
  })
}
</script>

<template>
  <div id="todoListPage" class="bg-half">
    <nav>
      <h1><a href="#">ONLINE TODO LIST</a></h1>
      <ul>
        <li class="todo_sm">
          <a href="#"><span>王小明的代辦</span></a>
        </li>
        <li><a href="#loginPage">登出</a></li>
      </ul>
    </nav>
    <div class="conatiner todoListPage vhContainer">
      <div class="todoList_Content">
        <div class="inputBox">
          <input type="text" placeholder="請輸入待辦事項" v-model="newTodo" />
          <a href="#" @click="addTodo()">
            <i class="fa fa-plus"></i>
          </a>
        </div>
        <div class="todoList_list">
          <ul class="todoList_tab">
            <li>
              <a href="#" :class="{ active: currentType === '全部' }" @click="changeType('全部')"
                >全部</a
              >
            </li>
            <li>
              <a
                href="#"
                :class="{ active: currentType === '待完成' }"
                @click="changeType('待完成')"
                >待完成</a
              >
            </li>
            <li>
              <a
                href="#"
                :class="{ active: currentType === '已完成' }"
                @click="changeType('已完成')"
                >已完成</a
              >
            </li>
          </ul>
          <div class="todoList_items">
            <ul class="todoList_item" v-for="todoList in todoListData" :key="todoList.id">
              <li>
                <label class="todoList_label">
                  <input
                    class="todoList_input"
                    type="checkbox"
                    value="todoList.value"
                    :checked="todoList.status"
                  />
                  <span>{{ todoList.name }}</span>
                </label>
                <a href="#" @click="removeItem(todoList.id)">
                  <i class="fa fa-times"></i>
                </a>
              </li>
            </ul>
            <div class="todoList_statistics">
              <p v-if="currentType === '待完成'">{{ todoListUnFinishCount }} 個待完成項目</p>
              <p v-else>{{ todoListFinishCount }} 個已完成項目</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
