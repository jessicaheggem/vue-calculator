<template>
  <div>
    <h1>Calculator</h1>
    <br />
    <div class="container wrap">
      <input class="display" />
      <br />
      <button
        v-for="b in buttons"
        :key="b.id"
        :style="[b.id === 1 ? lrgBtn: regBtn, b.number === true ? number: operator]"
        class="btn"
      >{{b.name}}</button>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      displayVal: 0,
      lrgBtn: {
        width: "40.5%",
        margin: "3px"
      },
      regBtn: {
        width: "20%",
        margin: "3px"
      },
      number: {
        backgroundColor: "yellow"
      },
      operator: {
        backgroundColor: "pink"
      },
      buttons: [
        {
          id: 1,
          name: "AC",
          number: false
        },
        {
          id: 2,
          name: "C",
          number: false
        },
        {
          id: 3,
          name: "/",
          number: false
        },
        {
          id: 4,
          name: "7",
          number: true
        },
        {
          id: 5,
          name: "8",
          number: true
        },
        {
          id: 6,
          name: "9",
          number: true
        },
        {
          id: 7,
          name: "x",
          number: false
        },
        {
          id: 8,
          name: "4",
          number: true
        },
        {
          id: 9,
          name: "5",
          number: true
        },
        {
          id: 10,
          name: "6",
          number: true
        },
        {
          id: 11,
          name: "-",
          number: false
        },
        {
          id: 12,
          name: "1",
          number: true
        },
        {
          id: 13,
          name: "2",
          number: true
        },
        {
          id: 14,
          name: "3",
          number: true
        },
        {
          id: 15,
          name: "+",
          number: false
        },
        {
          id: 16,
          name: "\u00b1",
          number: false
        },
        {
          id: 17,
          name: "0",
          number: true
        },
        {
          id: 18,
          name: ".",
          number: false
        },
        {
          id: 19,
          name: "=",
          number: false
        }
      ]
    };
  }
};
</script>

<style scoped>
.wrap {
  border: 1px;
  width: 50%;
}

.display {
  width: 82%;
}
.buttons.number {
  background-color: green;
}
.operator {
  background-color: pink !important;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
</style>
