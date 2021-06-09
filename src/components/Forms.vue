<template>
  <h1>Todo-List</h1>
  <div class="inputArea">
      <form action="" >
          <input type="text" placeholder="Please enter a word" v-model="newElem"/>
          <button @click.prevent="addElem">Add Element</button>
      </form>
  </div>
  <div class="generalStuff">
      <ul class="items">
          <li v-for="(word, index) in liste" :key="index" class="item"> {{ word }} <div class="removeItems" @click="removeElem(index)">&times;</div></li>
          
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Forms',
    data () {
        return {
            newElem: "",
            liste: ["Learn HTML", "Learn CSS", "Learn JavaScript"]
        }
    },
    methods: {
        addElem() {
            if(this.newElem !== '') {
               this.liste.push(this.newElem)
            }else {
                return
            }
            /* bereinigen meines Textfeldes */
            this.newElem="" 
            
        },
        removeElem(index) {
            /* this.liste[index].pop */
            this.liste.splice(index, 1)
            const prod = this.liste[index];
            console.log(`Removed: ${prod}`);
        }
    }

}
</script>

<style lang="scss" scoped>
    
    * {
        list-style: none;
    }

    .inputArea {
        display: flex;
        /* flex-direction: column; */
        justify-content: center;
        
        input {
            margin-right: 1rem;
        }
    }

    .generalStuff {
        width: 30%;
        margin: 0 auto;
        border: 1px solid gray;
        border-radius: 5px;
        margin-top: 2rem;
        padding: 2rem;

        .item {
            display: flex;
            justify-content: space-between;
        }

        .removeItems {
            cursor: pointer;
            font-weight: bold;
            color: red;
        }
    }
</style>