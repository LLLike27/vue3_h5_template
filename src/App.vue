<template>
  <!-- 暗黑主题 -->
  <!-- <van-config-provider theme="dark"></van-config-provider> -->
  <RouterView>
    <template #default="{ Component, route }">
      <transition name="slide-fade">
        <keep-alive v-if="route.meta.keepAlive">
          <component :is="Component" :key="route.path" />
        </keep-alive>
        <component v-else :is="Component" :key="route.path" />
        <!-- <component :is="Component" :key="route.path" /> -->
      </transition>
    </template>
  </RouterView>
</template>

<script setup>
import "vant/es/toast/style"
import "vant/es/dialog/style"
import "vant/es/notify/style"
import "vant/es/image-preview/style"
import "vant/lib/index.css"
</script>
<style lang="less">
// 全局样式
@import "@/styles/index.less";

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>
