<template>
  <!-- 컴퍼넌트 명명규칙은 Pascal Case 권장 -->
  <AppHeader 
    :appTitle="message"
    @change="changeMessage">
  </AppHeader>
</template>

<script>
// import 컴포넌트이름 from './컴포넌트 경로'
import AppHeader from './components/AppHeader.vue'

export default {
  components: {
    // '컴포넌트이름': 컴포넌트 내용
    // 'app-header': AppHeader,
    // 'AppHeader': AppHeader,
    // AppHeader: AppHeader,
    // key=value이면 value값만 써도 됨
    AppHeader
  },
  data() {
    return {
      message: '앱 헤더 컴포넌트'
    }
  },
  methods: {
    changeMessage() {
      this.message = '변경됨'
    }
  }
}
</script>

<style scoped>

</style>
