<template>
  <div id="app">
    <header>
      <nav>
        <ul>
          <li><a href="#" @click="selectedTab = 'post'; fetchUserPosts()">Post</a></li>
          <li><a href="#" @click="selectedTab = 'todos'">Todos</a></li>
        </ul>
      </nav>
    </header>

    <div class="container">
      <div v-if="selectedTab === 'post'" class="post-container">
        <h1 class="post-title">Postingan Pengguna</h1>
        <select v-model="selectedUser" @change="fetchUserPosts">
          <option v-for="user in users" :key="user.id" :value="user.id">{{ user.name }}</option>
        </select>
        <div v-for="post in userPosts" :key="post.id">
          <h2>{{ post.title }}</h2>
          <p>{{ post.body }}</p>
        </div>
      </div>

      <div v-if="selectedTab === 'todos'">
        <!-- Konten Todos -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedTab: 'post',
      kegiatanList: [],
      editedIndex: null,
      editedActivity: '',
      newActivity: '',
      filterActive: false,
      users: [],
      userPosts: [],
      selectedUser: null
    };
  },
  methods: {
    toggleFilter() {
      this.filterActive = !this.filterActive;
    },
    // Metode lainnya
  },
  created() {
    this.fetchUsers();
  }
};
</script>

<style>
/* Styling */
</style>
