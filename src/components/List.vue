<template>
  <div class="container">
    <h1>services</h1>
    <div>
      <ul>
        <li
          v-model="isActive"
          v-for="(list, id) in services"
          @click="total(list.id, list.amount)"
          :class="[list.isActive ? 'isActive' : '', 'list', list]"
        >
          <span>{{ list.title }}</span
          ><span>${{ list.amount }}</span>
        </li>
      </ul>
      <hr />
      <p>
        Total<span>{{ add }}</span>
      </p>
    </div>
  </div>
</template>
<script>
export default {
  name: 'List',
  data() {
    return {
      id: '',
      ans: '',
      amount: '',
      isActive: false,
      services: [
        { id: 1, title: 'Web Development ', amount: 300, isActive: false },
        { id: 2, title: 'Design ', amount: 400, isActive: false },
        { id: 3, title: 'Integration ', amount: 100, isActive: false },
        { id: 4, title: 'Tranning', amount: 200, isActive: false },
      ],
    }
  },

  methods: {
    total(id) {
      console.log(id, 'h')
      this.services = this.services.map((list) =>
        list.id === id ? { ...list, isActive: !list.isActive } : list
      )
    },
  },
  computed: {
    add() {
      const x = this.services.filter((list) => {
        if (list.isActive) {
          const a = list.amount
          return a
        }
      })
      var sum = 0
      x.forEach((e) => (sum += e.amount))
      return sum
    },
  },
}
</script>
<style scoped>
.container {
  display: block;
  margin: auto;
  border: 1px solid black;
  height: 45vh;
  width: 40%;
  background-color: rgb(107, 162, 199);
}
h1 {
  font-family: Cursive;
  color: white;
  font-size: 40px;
}
li {
  display: flex;
  align-items: center;
  padding: 2px;
  padding-left: 5px;
  padding-right: 5px;
  justify-content: space-between;
  list-style-type: none;
  height: 5vh;
  color: white;
  background-color: rgb(168, 77, 77);
  margin-top: 3px;
  margin-right: 15%;
  margin-left: 7%;
  cursor: pointer;
}
.list.isActive {
  background-color: green;
}

p {
  text-align: left;
  color: white;
  display: flex;
  justify-content: space-around;
}
li.selected {
  background-color: rgb(92, 141, 92);
}
</style>
