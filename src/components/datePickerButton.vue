<template>
  <div>
    <v-dialog max-width="500">
      <template v-slot:activator="{ props: activatorProps }">
        <v-btn
          v-bind="activatorProps"
          color="surface-variant"
          text="Chose date"
          variant="flat"
        ></v-btn>
      </template>

      <template v-slot:default="{ isActive }">
        <v-card title="Dialog">
          <v-card-text>
            <v-date-picker v-model="date"></v-date-picker>
          </v-card-text>

          <v-card-actions>
            <v-spacer></v-spacer>

            <v-btn text="Save" @click="isActive.value = false"></v-btn>
          </v-card-actions>
        </v-card>
      </template>
    </v-dialog>
  </div>
</template>
<script>
export default {
  name: "datePickerButton",
  emit: ["date"],
  data() {
    return {
      isActive: false,
      date: new Date(),
    };
  },
  watch: {
    date() {
      ;
      this.$emit("date", this.transformDate(this.date));
    },
  },
  methods: {
    transformDate(dateObject) {

      // Estrazione di giorno, mese e anno
      const day = dateObject.getDate();
      const month = dateObject.getMonth() + 1; // Nota: i mesi in JavaScript sono indicizzati da 0 a 11, quindi aggiungiamo 1
      const year = dateObject.getFullYear();

      // Formattazione della data nel formato gg/mm/aaaa
      const formattedDate = `${day
        .toString()
        .padStart(2, "0")}/${month.toString().padStart(2, "0")}/${year}`;
        return formattedDate
    },
  },
};
</script>
<style lang=""></style>
