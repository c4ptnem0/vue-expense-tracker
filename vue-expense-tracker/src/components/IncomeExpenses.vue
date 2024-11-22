<template>
  <div class="inc-exp-container">
    <div>
      <h4>Income</h4>
      <p id="money-plus" class="money plus">
        {{ formatCurrency(income ?? 0) }}
      </p>
    </div>
    <div>
      <h4>Expense</h4>
      <p id="money-minus" class="money minus">
        {{ formatCurrency(expenses ?? 0) }}
      </p>
    </div>
  </div>
</template>

<script setup>
import { defineProps, computed } from "vue";

const props = defineProps({
  income: {
    type: Number,
    required: true,
  },

  expenses: {
    type: Number,
    required: true,
  },
});

// Format as Philippine Peso currency
const formatCurrency = (value) => {
  return new Intl.NumberFormat("en-PH", {
    style: "currency",
    currency: "PHP",
  }).format(value);
};
</script>
