<template>
  <main class="max-w-2xl mx-auto px-4">
    <nav class="font-medium text-center text-gray-500 border-b border-gray-200 mb-4">
      <ul class="flex flex-wrap -mb-px">
        <li v-for="tab in tabs" :key="tab.key">
          <TabLink :tab="tab" :currentTab="currentTab" @click="currentTab = tab.key" />
        </li>
      </ul>
    </nav>
    <FadeTransition>
      <keep-alive>
        <component :is="currentTabComponent" />
      </keep-alive>
    </FadeTransition>
  </main>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import type { Tab, TabKey } from '@/types'
import TabLink from '@/components/TabLink.vue'
import GeneralSetting from '@/components/GeneralSetting.vue'
import NotificationsSetting from '@/components/NotificationsSetting.vue'
import PrivacySetting from '@/components/PrivacySetting.vue'
import FadeTransition from '@/components/FadeTransition.vue'

const tabs: Tab[] = [
  {
    key: 'General',
    label: 'General',
    component: GeneralSetting,
  },
  {
    key: 'Notifications',
    label: 'Notifications',
    component: NotificationsSetting,
  },
  {
    key: 'Privacy',
    label: 'Privacy',
    component: PrivacySetting,
  },
]
const currentTab = ref<TabKey>('General')
const currentTabComponent = computed(
  () => tabs.find((tab) => tab.key === currentTab.value)?.component,
)
</script>

<style scoped></style>
