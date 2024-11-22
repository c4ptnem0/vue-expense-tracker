<template>
  <h4>Your Balance</h4>
  <h1 id="balance">{{ formattedTotal }}</h1>
</template>

<script setup>
import { defineProps, computed } from "vue";

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});

const formatCurrency = (value) => {
  return new Intl.NumberFormat("en-PH", {
    style: "currency",
    currency: "PHP",
  }).format(value);
};

// Apply formatting
const formattedTotal = computed(() => formatCurrency(props.total));
</script>
