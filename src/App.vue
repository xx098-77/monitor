<template>
  <Layout :loading="loading">
    <template #left>
      <WidgetPanel04 title="湿地环境参数" />
      <WidgetPanel02 title="历史水位变化" />
      <WidgetPanel03 title="湿地植被覆盖率监测" />
    </template>

    <template #right>
      <WidgetPanel07
        v-show="current"
        :title="current + '详情'"
        :name="current"
      />
      <WidgetPanel06 v-show="!current" title="湿地监测总览" />
      <WidgetPanel01 name="污染检测" />
      <WidgetPanel05 title="湿地水质变化趋势" />
    </template>

    <template #middle>
      <div style="width: 100%; height: 100%" ref="container"></div>
    </template>
  </Layout>
</template>

<script setup lang="ts">
import {
  WidgetPanel01,
  WidgetPanel02,
  WidgetPanel03,
  WidgetPanel04,
  WidgetPanel05,
  WidgetPanel06,
  WidgetPanel07,
} from '@/components'
import { provide } from 'vue'
import { Layout } from '@/layout'
import { useWetland } from '@/hooks'  // 替换为新的 hooks

const {
  container,
  loading,
  current,
  // showPollutionAlert, // 可能的新方法
  // analyzeVegetationChange,
  // startMonitoring,
  // stopMonitoring,
} = useWetland() // 替换风力发电数据获取逻辑

provide('events', {
  // showPollutionAlert,
  // analyzeVegetationChange,
  // startMonitoring,
  // stopMonitoring,
})
</script>
