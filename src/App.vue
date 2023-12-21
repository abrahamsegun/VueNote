<script setup>
import { ref } from 'vue';
const ShowModel =  ref(false);
const ShowText = ref('')

const TodoNote= ref([])

function getRandomColor() {
 return  "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}



  const show =()=>{
    ShowModel.value = true

  }

  const addnote = (e)=>{


     if (ShowText.value === "" || ShowText.value.length === 1) {
      alert(`You can't add an empty note or a single word`)
       ShowModel.value = false
       return 
     }
    
    if (ShowText.value.length > 600) {
       ShowText.value = ""
       alert(`You can't add more than 600 words in a single note`)

       return 
    }
   
    TodoNote.value.push(
      {
        text: ShowText.value,
        date: new Date().toLocaleDateString('en-US'),
        backgroundColor :getRandomColor(),
        id:Math.floor(Math.random() * 1000000)
      }
    )

    ShowText.value =""
    return    ShowModel.value = false
  } 
</script>

<template>

  <section class=" section">
    <header>
  
      <div class="head">
        <div class="th">
          <h1 class="headt">Todo List App </h1>
        </div>
        <div class="tt">
          <h1 class="headp" @click="show">+</h1>
  
        </div>
      </div>
    </header>
  
    <main class="main">

       <div v-for="todo in TodoNote" class="todo" :style="{backgroundColor: todo.backgroundColor}">
      
            <div class="grido">
            {{todo.text  }}
             </div>

            <div class="date">
            {{ todo.date }}
            </div>

      
       </div>
      
    </main>
    <div v-if="ShowModel" class="display" id="displ">
      <div class="subdisplay">
        <div class="stubborn">
           <div  class="area" contentEditable="true">
            <textarea class="area1" v-model="ShowText" ></textarea>
             <div>
              {{  }}
             </div>
            </div>

        </div>
         <div class="disbtn">
            <button class="btn1" @click="addnote">Add Note</button>
            <button class="btn2" @click="ShowModel=false">Cancel</button>
         </div>
      </div>
         </div>

  </section>
</template>

<style scoped>

.head{
  display: flex;
  width: 100%;
  flex-direction: row;
  justify-content: space-around;
}
.headt{
  font-weight: bolder;
  font-size: 2.5rem;
  
}
.headp{
  font-size: 2.5rem;
  font-weight: 800;
  width: 3rem;
  cursor: pointer;
  background-color: rgb(69, 46, 46);
  display: flex;
  justify-content: center;
  color: white;
  border-radius: 50%;

}
.main{
  width: 100%;
  padding: 2rem;
  margin-top: 5rem;
  background-color: aqua;
  min-height: 50vh;
  margin:  5rem  auto 0;
  display: grid;
  grid-template-columns: 30% 30% 30%;
  column-gap: 3.3%;
  row-gap: 3rem;

}

.todo{
  min-height: 15rem;

 width: 100%;
 display: flex;
 flex-direction: column;
 justify-content: space-between;

 padding:0 1rem;
 text-wrap: wrap;
 /* overflow-x: hidden; */
 /* overflow-y: scroll; */
}

.todo{border: solid black 0.1rem;}
.display{
  width: 100%;
  min-height: 10rem;
  margin: auto;
  position: absolute;
  top: 30%;
  display: flex;
  justify-content: center;
  background-color: yellowgreen;
  padding: 2rem;

}
.grido{
  width: 100%;

  font-size: 2rem;
  text-wrap: wrap;
}
.subdisplay{
  width: 60%;
  min-height: fit-content;
 

}
.date{
  font-size: 1.3rem;
  font-weight: bold;
}
.stubborn{
    width: 100%;
    height: fit-content;
    margin-bottom: 2rem;
}
.area{
 background-color: blanchedalmond;
  min-height: 10rem;
  padding: 1rem;
  font-size: 1.7rem;
}
.area1{
  width: 100%;
  background-color: blanchedalmond;
  min-height: 10rem;
  font-size: 1.7rem;
  box-sizing: border-box;
  height: 100%;
  resize: none;
}

.section{
  position: relative;

}
.disbtn{
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: .5rem;
 
}
.btn1{
 min-width: 100%; 
 height: 2.5rem;
 background-color: rgb(173, 173, 192);
 color: white;
 font-size: 1.5rem;
 cursor: pointer;
  font-weight: bolder;
}
.btn2{
  min-width: 100%;
  height: 2.5rem;
  color: white;
  cursor: pointer;
  font-size: 1.5rem;
  font-weight: bolder;
  background-color: rgb(195, 92, 92);
}
@media screen and (max-width: 774px) {
   
  .main{
  width: 100%;
  padding: 2rem;
  margin-top: 5rem;
  background-color: aqua;
  min-height: 50vh;
  margin:  5rem  auto 0;
  display: grid;
  grid-template-columns: 90%;
  column-gap: 10%;
  row-gap: 3rem;

}
.grido{
  width: 100%;

  font-size: 1.4rem;
  text-wrap: wrap;
}

}
@media screen and (max-width: 1200px) and (min-width: 775px) {
  
  .main{
  width: 100%;
  padding: 2rem;
  margin-top: 5rem;
  background-color: aqua;
  min-height: 50vh;
  margin:  5rem  auto 0;
  display: grid;
  grid-template-columns: 45% 45%;
  column-gap: 5%;
  row-gap: 3rem;

}
.grido{
  width: 100%;

  font-size: 1.6rem;
  text-wrap: wrap;
}
}
</style>
