<template>
  <div>
    <h1>Calculator</h1>
    <br />
    <div class="container wrap">
      <input class="display text-right" style="font-size: 18px;" :value="displayVal"/>
      <br />
      <button
        v-for="b in buttons"
        :key="b.id"
        :style="[regBtn, b.number === true ? number: operator]"
        class="btn"
      >{{b.name}}</button>
    </div>
    <br>
    <div>
      <h4>Display active functions here:</h4>
      <p>{{displayVal}}</p>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      displayVal: 0,
      regBtn: {
        width: "20%",
        margin: "3px"
      },
      number: {
        backgroundColor: "lightBlue"
      },
      operator: {
        backgroundColor: "lightGray"
      },
      buttons: [
        {
          id: 1,
          name: "7",
          number: true
        },
        {
          id: 2,
          name: "8",
          number: true
        },
        {
          id: 3,
          name: "9",
          number: true
        },
          {
          id: 4,
          name: "/",
          number: false
        },
        
        {
          id: 5,
          name: "4",
          number: true
        },
        {
          id: 6,
          name: "5",
          number: true
        },
        {
          id: 7,
          name: "6",
          number: true
        },
        {
          id: 8,
          name: "x",
          number: false
        },
       
        {
          id: 9,
          name: "1",
          number: true
        },
        {
          id: 10,
          name: "2",
          number: true
        },
        {
          id: 11,
          name: "3",
          number: true
        },
         {
          id: 12,
          name: "-",
          number: false
        },
         {
          id: 13,
          name: "C",
          number: false
        },
         {
          id: 14,
          name: "0",
          number: true
        },
         {
          id: 15,
          name: "=",
          number: false
        },
        {
          id: 16,
          name: "+",
          number: false
        },
      ],
      methods: {
        minus: function(){
          console.log('clicked minus');
          
        },
        add: function(){
          console.log('clicked add');
          
        },
        divide: function(){
          console.log('clicked divide');
          
        },
        multiply: function(){
          console.log('clicked multiply');
          
        },
        equals: function(){
          console.log('clicked equals');
          
        },
        clear: function(){
          console.log('clicked clear');
          
        },
        
      }
    };
  }
};
</script>

<style scoped>
.wrap {
  border: 1px;
  width: 30%;
}

.display {
  width: 84%;
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
