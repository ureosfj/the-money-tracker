<script setup lang="ts">
import { ref } from "vue";
import transactionDetail from "@/components/transactionDetail.vue";
const transactions = ref([
  { digits: 200, category: "ecommerce", type: "income" },
  { digits: 300, category: "investment", type: "income" },
  { digits: 400, category: "salary", type: "income" },
  { digits: 33, category: "shopping", type: "expense" },
  { digits: 45, category: "shopping", type: "expense" },
]);

const addNewTransaction = (data) => {
  transactions.value.push(data);
};
</script>
<template>
  <div>
    <p class="text-center">Transactions</p>
    <v-table>
      <thead>
        <tr>
          <th class="text-left">Amount</th>
          <th class="text-left">Category</th>
          <th class="text-left">Type</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(t, i) in transactions" :key="i">
          <td>{{ t.digits }}</td>
          <td>{{ t.category }}</td>
          <td>{{ t.type }}</td>
        </tr>
      </tbody>
    </v-table>
    <transactionDetail @new="addNewTransaction"></transactionDetail>
  </div>
</template>
<style></style>
