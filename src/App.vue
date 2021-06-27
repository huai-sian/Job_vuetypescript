<template>
  <div class="app">
    <button @click.prevent="handleClick('title')">Order by title</button>
    <button @click.prevent="handleClick('salary')">Order by salary</button>
    <button @click.prevent="handleClick('location')">Order by location</button>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref} from 'vue';
import Job from '@/type/Job';
import JobList from '@/components/jobList.vue';
import OrderTerm from '@/type/OrderTerm';

export default defineComponent({
  name: 'App',
  components: {
    JobList
  },
  data() {
    return {
      name: 'Link',
      age: 25 as number | string
    }
  },
  setup(){
    /* const state = reactive({
      nombre: 'Luis', // automatically as stirng
      edad: 23 as number | string // also can declare type with 'as ...'
    })
    state.nombre = 'Carlos'; // has to be string
    return{ ...toRefs(state)}

    const name = ref('link');
    const age = ref<number | string>(23); //age is a reference object, type send by generics
    return{ name, age }; */

    const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
    ])
    const order = ref<OrderTerm>('title');
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return { jobs, handleClick, order };
  },
  methods: {
    changeName(name: string){
      this.name = name;
      return name;
    },
    changeAge(age: number){
      this.age = age;
      return age;
    }
  }
});
</script>

<style>

</style>
