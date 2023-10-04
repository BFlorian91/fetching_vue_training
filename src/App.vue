<template>
  <h1>Test Fetching VueJS</h1>
  <div class="container">
    <div class="container__child">
      <div class="card" v-for="item in data" :key="item.id">
        <Card :id="item.id" :title="item.name" :email="item.email" :username="item.username" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Card from './components/Card.vue';

interface DataItem {
  id: number;
  name: string;
  email: string;
  username: string;
}

export default defineComponent({
    data() {
        return {
            data: [] as DataItem[]
        };
    },
    mounted() {
        fetch("https://jsonplaceholder.typicode.com/users")
            .then(response => {
            if (!response.ok) {
                throw new Error("Failed to fetch");
            }
            return response.json();
        })
            .then((data: DataItem[]) => {
            this.data = data;
        })
            .catch(error => {
            console.error("Fetch error: ", error);
        });
    },
    components: { Card }
});
</script>

<style scoped>
 h1 {
   text-align: center;
   color: rgb(31, 162, 114);
 }
  .container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }
  .container__child {
    width: 320px;
    color: white;
    padding: 1rem;
    margin: 1rem;
  }
  .card {
    display: flex;
    background-color: rgb(31, 162, 114);
    padding: 1rem;
    margin: 1rem;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    transition: transform 0.2s;
  }
  .card:hover {
    background-color: rgb(31, 162, 114, 0.8);
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.4);
    transform: translateY(-5px);
  }
</style>