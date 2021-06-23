<template>
  <v-container class="page">
    <!-- Title -->
    <div class="page-title">Расписание уроков</div>

    <!-- Top actions -->
    <v-row
      class="margin-top-10"
      dense>
      <v-col
        dense
        align-self="end"
        cols="3">
        <v-select
          class="flex-grow-0 no-bottom"
          outlined
          dense
          clearable
          :items="['A', 'B', 'C']"
          label="Выберите класс">
        </v-select>
      </v-col>
      <v-spacer />
      <v-col
        dense
        align-self="end"
        cols="auto">
        <v-btn
          class="button-copy"
          dark
          rounded
          depressed>
          Скопировать расписание
        </v-btn>
      </v-col>
    </v-row>

    <!-- Weeks -->
    <WeeksBar class="margin-top-20" :currentWeek="9" :totalWeeks="10" />

    <!-- Days -->
    <DaysGrid class="margin-top-36" />
  </v-container>
</template>

<script>
import WeeksBar from '@/components/WeeksBar';
import DaysGrid from '@/components/DaysGrid';

export default {
  layout: 'default',
  components: {
    WeeksBar,
    DaysGrid,
  }
}
</script>

<style lang="scss" scoped>
.margin-top-10 {
  margin-top: 10px;
}

.margin-top-20 {
  margin-top: 20px;
}

.margin-top-36 {
  margin-top: 36px;
}

.page {
  padding: 12px 10px;
  padding-bottom: 196px;
}

.page-title {
  font-family: Roboto;
  font-style: normal;
  font-weight: bold;
  font-size: 26px;
  line-height: 30px;
  color: black;
  margin-top: 130px;
}

.no-bottom {
  ::v-deep {
    .v-input__slot {
      margin-bottom: 0;
    }

    .v-text-field__details {
      display: none;
    }
  }
}

.button-copy {
  height: auto !important;
  padding: 15px 32px !important;
  background-color: #1864AB !important;
  font-family: Roboto;
  font-style: normal;
  font-weight: bold;
  font-size: 18px;
  line-height: 21px;
  text-align: center;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}
</style>
