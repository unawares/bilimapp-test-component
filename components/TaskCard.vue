<template>
  <v-card
    class="task-card select" :class="{invalid: hasError}">
    <div class="task-card-text">
      <div class="tag noselect">{{ data.tag }}</div>
      <div class="subject">{{ data.subject }}</div>
      <div v-if="data.given != null" class="given">{{ data.given }}</div>
      <div v-else class="given-invalid">
        <div class="not-given">
          <div class="not-given-icon">
            <v-icon class="icon" small>mdi-account-circle</v-icon>
          </div>
          <div class="not-given-text">
            Не задан
          </div>
        </div>
      </div>
      <div class="author" :class="{invalid: data.author == null }">
        <div class="author-icon">
          <v-icon class="icon" small>mdi-account-circle</v-icon>
        </div>
        <div class="author-name">
          {{ data.author != null ? data.author : 'Не задан'}}
        </div>
      </div>
    </div>
    
    <div class="task-card-actions noselect">
      <v-btn
        class="button"
        small
        icon
      >
        <v-icon class="icon" small>mdi-pencil</v-icon>
      </v-btn>

      <v-btn
        class="button"
        small
        icon
      >
        <v-icon class="icon" small>mdi-eye</v-icon>
      </v-btn>
    </div>
  </v-card>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      required: true,
    },
  },

  computed: {
    hasError () {
      if (this.data.given == null) {
        return true;
      }
      if (this.data.author == null) {
        return true;
      }
      return false;
    },
  },
}
</script>

<style lang="scss" scoped>
.task-card-text {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  flex-grow: 1;
}

.task-card-actions {
  margin-top: 10px;
}

.tag {
  display: inline-block;
  background-color: #EFF7FF;
  color: #1864AB;
  padding: 5px 12px;
  border-radius: 9999px;
  font-family: Roboto;
  font-style: normal;
  font-weight: bold;
  font-size: 10px;
  line-height: 100%;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.subject {
  color: black;
  margin-top: 10px;
  font-family: Roboto;
  font-style: normal;
  font-weight: bold;
  font-size: 16px;
  line-height: 100%;
}

.given {
  color: black;
  margin-top: 10px;
  font-family: Roboto;
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 100%;
  flex-grow: 1;
}

.author {
  margin-top: 10px;
  display: inline-flex;
  align-items: center;

  .author-icon {
    transform: translateY(-2px);

    .icon {
      color: #1864AB;
    }
  }

  .author-name {
    margin-left: 4px;
    color: black;
    font-family: Roboto;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 100%;
  }

  &.invalid {
    .icon {
      color: #FD4A4A;
    }

    .author-name {
      color: #FD4A4A;
    }
  }
}

.given-invalid {
  flex-grow: 1;
}

.not-given {
  display: inline-flex;
  align-items: center;

  .not-given-icon {
    transform: translateY(-2px);

    .icon {
      color: #FD4A4A;
    }
  }

  .not-given-text {
    margin-left: 4px;
    color: #FD4A4A;;
    font-family: Roboto;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 100%;
  }
}

.button {
  background-color: #EBF5FF;

  .icon {
    color: #1864AB;
  }

  &:not(:first-child) {
    margin-left: 4px;
  }
}

.task-card {
  padding: 23px 20px 18px;
  box-shadow: 0px 4px 30px rgba(0, 72, 180, 0.15) !important;
  border-radius: 20px !important;
  display: flex;
  flex-direction: column;

  &.invalid {
    background-color: #FFD4D4;

    .tag, .button {
      background-color: #FFEBEB;
    }
  }
}
</style>
