<template>
  <div class="container">
    <h1>services</h1>
    <div>
      <ul>
        <li
          v-model="isActive"
          v-for="(list, index) in services"
          @click="active(index)"
          :class="[list.isActive ? 'green' : 'red']"
        >
          <span>{{ list.title }}</span
          ><span>${{ list.amount }}.00</span>
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
    active(index) {
      this.services[index].isActive = !this.services[index].isActive
    },
  },

  computed: {
    add() {
      var sum = 0
      this.services.filter((e) => {
        if (e.isActive) {
          sum += e.amount
          console.log(sum)
        }
      })
      return sum
    },
  },
}
</script>
<style scoped>
* {
  font-weight: bold;
}
.container {
  display: block;
  margin: auto;
  margin-top: 20%;
  border: 1px solid black;
  border-radius: 5px;
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
  padding-left: 20px;
  padding-right: 20px;
  justify-content: space-between;
  list-style-type: none;
  height: 5vh;
  color: white;
  background-color: rgb(192, 104, 104);
  margin-top: 5px;
  margin-right: 15%;
  margin-left: 7%;
  cursor: pointer;
}
.list.isActive {
  background-color: rgb(129, 167, 98);
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
.green {
  background-color: green;
}
.red {
  background-color: rgb(192, 104, 104);
}
</style>
