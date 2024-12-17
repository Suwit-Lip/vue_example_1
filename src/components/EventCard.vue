<template>
  <SectionCard>
    <template #header>
      {{ title }}
    </template>
    {{ when }}
    <template #footer>
      <div class="space-y-4">
        <p>{{ description }}</p>
        <section class="flex justify-end p-4">
          <RoundButton @click="$emit('register')">Register</RoundButton>
        </section>
      </div>
    </template>
  </SectionCard>
</template>
<script setup>
import RoundButton from '@/components/RoundButton.vue';
import SectionCard from '@/components/SectionCard.vue';
defineProps({
  title: String,
  when: String,
  description: String,
});
defineEmits(['register']);
</script>
