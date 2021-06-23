<template>
  <v-sheet
    class="d-flex flex-row justify-center weeks-bar">

    <div class="action" :class="{visible: hasPrev}" @click="prev">
      <v-icon
        class="icon"
        large
      >
        mdi-chevron-left
      </v-icon>
    </div>
    
    <div v-for="week in weeks" :key="week" class="week" :class="{
      exists: week != null,
      active: week === currentWeek
    }">
      <template v-if="week != null">
        <div class="week-top">{{ week }} неделя</div>
        <div class="week-bottom">10 - 16 май 2021</div>
      </template>
    </div>

    <div class="action" :class="{visible: hasNext}" @click="next">
      <v-icon
        class="icon"
        large
      >
        mdi-chevron-right
      </v-icon>
    </div>

  </v-sheet>
</template>

<script>
export default {
  props: {
    currentWeek: {
      type: Number,
      required: true,
    },

    totalWeeks: {
      type: Number,
      required: true,
    },
  },

  data () {
    return {
      offset: 0,
      limit: 6,
    }
  },

  computed: {
    isActionsVisible () {
      return this.limit < this.totalWeeks;
    },

    hasPrev () {
      return this.isActionsVisible && this.offset > 0;
    },

    hasNext () {
      return this.isActionsVisible && (this.offset + this.limit < this.totalWeeks);
    },

    weeks () {
      return Array.from(
        {length: Math.max(this.totalWeeks, this.limit)},
        (x, i) => (i < this.totalWeeks) ? i + 1 : null,

      ).slice(this.offset, Math.min(this.offset + this.limit, Math.max(this.totalWeeks, this.limit)));
    },
  },

  created () {
    let startOffset = Math.floor((this.currentWeek - 1) / this.limit) * this.limit;
    this.offset = Math.min(startOffset, Math.max(this.totalWeeks - this.limit, 0));
  },

  methods: {
    next () {
      this.offset = Math.min(this.offset + this.limit, Math.max(this.totalWeeks - this.limit, 0));
    },

    prev () {
      this.offset = Math.max(this.offset - this.limit, 0);
    },
  }
}
</script>

<style lang="scss" scoped>
.weeks-bar {
  padding: 0 12px;
  box-shadow: 0px 4px 30px rgba(0, 72, 180, 0.15);
  border-radius: 25px;
}

.week, .action {
  margin: 23px 12px;
  padding: 4px 19px 8px;
  border-radius: 9999px;
  border: 1px solid transparent;
}

.action {
  pointer-events: none;
  visibility: hidden;
  margin: 23px 0;
  padding: 4px 11px 8px;

  &.visible {
    cursor: pointer;
    pointer-events: all;
    visibility: visible;
  }
}

.week {
  pointer-events: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 130px;

  .week-top {
    font-family: Roboto;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .week-bottom {
    font-family: Roboto;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  &.exists {
    cursor: pointer;
    pointer-events: all;
    
    &:hover {
      $hover-opacity: 0.5;

      background-color: rgba($color: #F5FAFF, $alpha: $hover-opacity);
      border: 1px solid rgba($color: #1864AB, $alpha: $hover-opacity);

      .week-top {
        color: #1864AB;
      }

      .week-bottom {
        color: #1864AB;
      }
    }

    &.active {
      background-color: #F5FAFF;
      border: 1px solid #1864AB;

      .week-top {
        color: #1864AB;
        font-weight: bold;
      }

      .week-bottom {
        color: #1864AB;
      }
    }
  }
}

.action {
  display: flex;
  justify-content: center;
  align-items: center;
  
  .icon {
    color: #000000;
  }

  &:hover {
    .icon {
      color: #1864AB;
    }
  }
}
</style>