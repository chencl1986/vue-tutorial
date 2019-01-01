<template>
  <div>
    <div>a: {{a}}</div>
    <div>b: {{b}}</div>
    <div>count from getters: {{$store.getters.count}}</div>
    <div>count from computed: {{countFromComputed}}</div>
    <div>count from computed: {{countFromComputedSet}}</div>
    <div>count: {{count}}</div>
    <input type="button" value="count+5" @click="addCount(5)" />
  </div>
</template>

<script>
import Table from '@/components/common/Table';
import Cmp1 from '@/components/Cmp1';
import {mapState, mapActions, mapGetters} from 'vuex';

export default {
  name: 'Index',
  data () {
    return {
      fields: [
        {name: 'ID', text: 'ID'},
        {name: 'name', text: '姓名'},
        {name: 'age', text: '年龄'},
      ],
      datas: [
        {ID: 1, name: 'blue', age: 18},
        {ID: 2, name: '张三', age: 25},
        {ID: 4, name: 'tom', age: 8},
      ]
    }
  },
  async created(){
    await this.readUsers();

    //this.setStr('sdfasdfsdg');
  },
  methods: {
    addCount(value) {
      this.countFromComputedSet += 5
    },
  },
  components: {
    Table, Cmp1
  },
  computed: {
    countFromComputed() {
      return this.$store.getters.count
    },
    countFromComputedSet: {
      get() {
        return this.$store.getters.count
      },
      set(value) {
        this.$store.dispatch('addA', 5)
      },
    },
  }
}
</script>

<style scoped>
</style>
