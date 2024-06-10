<template>
  <div>
    <v-dialog width="500">
      <template v-slot:activator="{ props }">
        <v-btn v-bind="props" color="primary" text="Add transaction"> </v-btn>
      </template>

      <template>
        <v-card title="Dialog">
          <v-form v-slot:default="{ isActive }">
            <v-container>
              <v-row>
                <v-text-field
                  v-model="transaction.description"
                  :counter="10"
                  label="Description"
                  required
                  hide-details
                ></v-text-field>
              </v-row>
              <v-row>
                <v-text-field
                  v-model="transaction.category"
                  :counter="10"
                  label="Category"
                  hide-details
                  required
                ></v-text-field>
              </v-row>
              <v-row>
                <v-text-field
                  v-model="transaction.bank"
                  label="Bank account"
                  hide-details
                  required
                ></v-text-field>
              </v-row>
              <v-row>
                <v-text-field
                  v-model="transaction.type"
                  label="Type of transaction"
                  hide-details
                  required
                ></v-text-field>
              </v-row>
              <v-row>
                <v-text-field
                  v-model="transaction.amount"
                  label="Amount"
                  hide-details
                  required
                ></v-text-field>
              </v-row>
              <v-row>
                <v-text-field
                  v-model="transaction.date"
                  label="Date"
                  hide-details
                  required
                  readonly
                ></v-text-field>
                <datePickerButton @date="transaction.date = $event"></datePickerButton>
              </v-row>
              <v-row>
                <v-text-field
                  v-model="transaction.note"
                  label="Note"
                  hide-details
                  required
                ></v-text-field>
              </v-row>
            </v-container>
          </v-form>

          <v-card-actions>
            <v-spacer></v-spacer>

            <v-btn text="Save" @click="save"></v-btn>
          </v-card-actions>
        </v-card>
      </template>
    </v-dialog>
  </div>
</template>

<script setup>
import { ref, reactive, defineEmits } from "vue";
import datePickerButton from "./datePickerButton.vue";
const transaction = reactive({});
const isActive = ref(false);
const emits = defineEmits(["new"]);
const save = () => {
  isActive.value = false;
  emits("new", transaction);
};
</script>

<style></style>
