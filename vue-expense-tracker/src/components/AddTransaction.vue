<template>
  <h3>Add new transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Description</label>
      <input
        type="text"
        id="text"
        v-model="text"
        placeholder="Enter a description (e.g., Salary, Rent)"
      />
    </div>
    <div class="form-control">
      <label for="amount"
        >Amount <br />
        (negative - expense, positive - income)</label
      >
      <input
        type="text"
        id="amount"
        v-model="amount"
        placeholder="Enter an amount (e.g., -500 for expenses)"
      />
    </div>
    <button class="btn">Add transaction</button>
  </form>
</template>

<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";

const text = ref("");
const amount = ref("");
const emit = defineEmits(["transactionSubmitted"]);
const toast = useToast();

const onSubmit = () => {
  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  if (!text.value.trim() || !amount.value.trim()) {
    toast.error("Both fields must be filled!");
    return;
  }

  if (isNaN(amount.value)) {
    toast.error("Amount must be a number!");
  } else {
    emit("transactionSubmitted", transactionData);
  }

  text.value = "";
  amount.value = "";
};
</script>
