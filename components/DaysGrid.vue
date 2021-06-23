<template>
  <div class="days-grid">
    <div v-for="day in ['Понедельник', 'Вторник', 'Среда', 'Четверг' ,'Пятница']" :key="day" class="day">
      <div class="label">{{ day }}</div>
      <div class="date">10 май 2021</div>
    </div>
    <template v-for="(item, index) in gridItems">
      <div v-if="item == null" :key="`none_${index}`" class="none"></div>
      <EmptyCard v-else-if="item == 'new'" :key="`new_${index}`" />
      <TaskCard v-else :data="item" :key="item.id" />
    </template>
  </div>
</template>

<script>
import TaskCard from '@/components/TaskCard';
import EmptyCard from '@/components/EmptyCard';

export default {
  components: {
    TaskCard,
    EmptyCard,
  },

  data () {
    return {
      tasks: [
        {
          id: 1,
          date: new Date('2000-12-17T03:24:00'),
          tag: "Урок BILIMLAND",
          subject: "Геометрия",
          given: "Екі айнымалысы бар сызықтық теңдеулер жүйесін қосу тәсілімен және алмастыру тәсілімен шешу. 8-сабақ",
          author: "Ташманова Роза",
        },
        {
          id: 2,
          date: new Date('2000-12-17T03:24:00'),
          tag: "Урок BILIMLAND",
          subject: "Математика",
          given: "Екі айнымалысы бар сызықтық теңдеулер жүйесін қосу тәсілімен және алмастыру тәсілімен шешу. 8-сабақ",
          author: null,
        },
        {
          id: 3,
          date: new Date('2000-12-18T03:24:00'),
          tag: "Урок BILIMLAND",
          subject: "Математика",
          given: "Екі айнымалысы бар сызықтық теңдеулер жүйесін қосу тәсілімен және алмастыру тәсілімен шешу. 8-сабақ",
          author: "Ташманова Роза",
        },
        {
          id: 4,
          date: new Date('2000-12-19T03:24:00'),
          tag: "Урок BILIMLAND",
          subject: "Математика",
          given: "Екі айнымалысы бар сызықтық теңдеулер жүйесін қосу тәсілімен және алмастыру тәсілімен шешу. 8-сабақ",
          author: "Ташманова Роза",
        },
        {
          id: 5,
          date: new Date('2000-12-19T03:24:00'),
          tag: "Урок BILIMLAND",
          subject: "Математика",
          given: null,
          author: "Ташманова Роза",
        },
        {
          id: 6,
          date: new Date('2000-12-19T03:24:00'),
          tag: "Урок BILIMLAND",
          subject: "Математика",
          given: "Екі айнымалысы бар сызықтық теңдеулер жүйесін қосу тәсілімен және алмастыру тәсілімен шешу. 8-сабақ",
          author: "Ташманова Роза",
        },
        {
          id: 11,
          date: new Date('2000-12-19T03:24:00'),
          tag: "Урок BILIMLAND",
          subject: "Математика",
          given: "Екі айнымалысы бар сызықтық теңдеулер жүйесін қосу тәсілімен және алмастыру тәсілімен шешу. 8-сабақ",
          author: "Ташманова Роза",
        },
        {
          id: 2,
          date: new Date('2000-12-17T03:24:00'),
          tag: "Урок BILIMLAND",
          subject: "Математика",
          given: "Екі айнымалысы бар сызықтық теңдеулер жүйесін қосу тәсілімен және алмастыру тәсілімен шешу. 8-сабақ",
          author: null,
        },
      ],
    };
  },

  computed: {
    gridItems () {
      const startWeekDay = 0;
      const endWeekDay = 4;

      let mp = {}

      for (let i = startWeekDay; i <= endWeekDay; i++) {
        mp[i] = [];
      }

      for (let task of this.tasks) {
        let weekDay = task.date.getDay();

        if (weekDay >= startWeekDay && weekDay <= endWeekDay) {
          mp[weekDay].push(task);
        }
      }

      for (let i = startWeekDay; i <= endWeekDay; i++) {
        mp[i].push('new');
      }

      let orderedItems = [];

      while (true) {
        let hasNext = false;
        for (let i = startWeekDay; i <= endWeekDay; i++) {
          if (mp[i].length > 0) {
            let item = mp[i].shift();
            orderedItems.push(item);
          } else {
            orderedItems.push(null);
          }
          
          if (mp[i].length > 0) {
            hasNext = true;
          }
        }

        if (!hasNext) {
          break;
        }
      }

      return orderedItems;
    },
  },
}
</script>

<style lang="scss" scoped>
.days-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-auto-rows: auto;
  grid-gap: 20px;
}

.day {
  display: inline-flex;
  flex-direction: column;
  align-items: center;

  .label {
    font-family: Roboto;
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 150%;
  }

  .date {
    font-family: Roboto;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
  }
}
</style>
