<template>
  <el-card :body-style="{ padding: '0px' }" shadow="hover" v-for="item in prop.list" :key="item.id" v-once
           @click="getPlaylistDetail(item.id)">
    <svg-icon icon-class="playMusic"/>
    <el-image class="listImg" :src="item.picUrl ? item.picUrl + '?param=200y200': item.cover" lazy/>
    <el-image :src="item.picUrl ? item.picUrl + '?param=200y60': item.cover" style="filter: blur(30px)" lazy/>
    <el-text class="listInfo">{{ item.name }}</el-text>
  </el-card>
</template>

<script setup lang="ts">
// 公用获取歌单详情的函数
import {getPlaylistDetail} from "@/utils/playlist";

const prop = defineProps(['list'])

</script>

<style scoped>
.el-card {
  position: relative;
  overflow: hidden;
  display: inline-block;
  width: 200px;
  height: 260px;
  margin: 0 2rem 2rem 0;
  border-radius: 10px;
  cursor: pointer;
  color: #FFFFFF;
}

.listImg {
  display: block;
  width: 100%;
  height: 100%;
  transition: filter .3s;
}

.listInfo {
  color: #000000;
  position: absolute;
  display: block;
  width: 100%;
  height: 60px;
  bottom: 0;
  padding: .5rem;
  backdrop-filter: blur(30px);
}

.svg-icon {
  position: absolute;
  z-index: 1;
  font-size: 50px;
  bottom: 70px;
  right: 10px;
  transform: scale(0.5);
  opacity: 0;
  transition: transform .3s;
}

.el-card:hover .listImg {
  filter: brightness(.6);
}

.el-card:hover .svg-icon {
  opacity: 1;
  transform: scale(1);
}
</style>