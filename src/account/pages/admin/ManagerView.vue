<template>
    <v-container>
      <h1>회원 정보 관리</h1>
      <v-data-table
        :headers="headers"
        :items="users"
        item-key="id"
        class="elevation-1"
      >
        <template v-slot:top>
          <v-toolbar flat>
            <v-toolbar-title>회원 목록</v-toolbar-title>
            <v-divider
              class="mx-4"
              inset
              vertical
            ></v-divider>
            <v-spacer></v-spacer>
            <v-btn color="primary" @click="fetchUsers">새로고침</v-btn>
          </v-toolbar>
        </template>
      </v-data-table>
    </v-container>
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted } from 'vue';
  import axios from 'axios';
  
  const headers = ref([
    { text: 'ID', value: 'id' },
    { text: '아이디', value: 'username' },
    { text: '닉네임', value: 'nickname' },
    { text: '이름', value: 'name' },
    { text: '이메일', value: 'email' },
    { text: '성별', value: 'gender' },
    { text: 'MBTI', value: 'MBTI' },
    { text: '로그인 타입', value: 'LoginType'},
  ]);
  
  const users = ref([]);
  
  const fetchUsers = async () => {
    try {
      const response = await axios.get('/api/users'); // 예시 API 엔드포인트
      users.value = response.data;
    } catch (error) {
      console.error('Failed to fetch users:', error);
    }
  };
  
  onMounted(() => {
    fetchUsers();
  });
  </script>
  
  <style scoped>
  h1 {
    margin-bottom: 20px;
    font-size: 24px;
    font-weight: bold;
  }
  
  .v-data-table {
    margin-top: 20px;
  }
  </style>