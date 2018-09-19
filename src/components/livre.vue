<template>
<div>

<div id="div1" @drop.self="drop($event)" @dragover="allowDrop($event)">

 <div class="silence" draggable="true" @dragstart="drag($event)" id="drag1"  >

 <div class="centrage">
      <b> Silence :</b> il s’agit de maitriser notre conscience et réduire notre stress en méditant, priant, respirant, réfléchissant…
   </div>
</div>
 <div class="affirmation" draggable="true" @dragstart="drag($event)" id="drag2" >
<div class="centrage">
<b>Affirmation :</b> il faut répéter à voix haute, écrire, imaginer, des affirmations sur la personne que nous voulons devenir

   </div>
   </div>
 <div class="visualisation" draggable="true" @dragstart="drag($event)" id="drag3" >
<div class="centrage">
<b>Visualisation :</b>
 cela consiste à imaginer ce que nous voulons devenir et de nous imaginer en train de l’accomplir

   </div>
   </div>
 <div class="Exercice" draggable="true" @dragstart="drag($event)" id="drag4" >
<div class="centrage">
<b>Exercice :</b> non il ne s’agit pas d’exercice de mathématique mais bien d’exercice physique, de sport, de se bouger les fesses, que ce soit en marchant, en courant, en faisant des exercices chez soi ou en allant dans une salle de sport

   </div>
   </div>
 <div class="lecture" draggable="true" @dragstart="drag($event)" id="drag5" >
<div class="centrage">

<b>Lecture :</b> afin d’acquérir des connaissances Hal recommande de lire chaque matin quelques pages d’un livre de non fiction


</div></div>
 <div class="ecrire"  draggable="true" @dragstart="drag($event)" id="drag6" :style="graph">

<div class="centrage">
<b>Ecrire :</b> tenir un journal et y écrire chaque matin nos idées, nos projets, ce pourquoi nous sommes reconnaissant, ce qui nous rends heureux

</div></div>

</div>
<div id="div2" @drop="drop($event)" @dragover="allowDrop($event)"></div>




   </div>


</template>
<script>
export default {
  data() {
    return{
 avant: true,
graph:{
position:'relative',
top:0,
left:0


}
 }







  },
 computed: {
    computed_class() {
      if (this.avant) {
        return { avant: this.avant };
      } else {
        return { après: !this.avant };
      }
    }},

methods:{
allowDrop(ev) {
    ev.preventDefault();

},
graph1(ev){

  if (ev!=undefined)
  {
 var tran = "";
var trantop="";
var tranleft="";
 /* if (ev.currentTarget.id==="div2"){*/




     tran='fixed';
    trantop=ev.clientX+"px";
     tranleft=ev.clientY+"px";

                    }else{


                                  tran= 'relative'
                                trantop="0";
     tranleft="0";
                          }
return{

     position:tran,
    top:trantop,
     left:tranleft
      }

          },

 drag(ev) {
    ev.dataTransfer.setData("text", ev.target.id);

},
 drop(ev) {
    ev.preventDefault();


    var indexchild=0;
    var data = ev.dataTransfer.getData("text");
var data2=ev.clientY;
if (ev.target.childNodes.length===0){
   ev.target.insertBefore(document.getElementById(data),ev.target.firstChild);}
   else{
     for (var i=0;i<ev.target.childNodes.length;i++){
       if (ev.target.childNodes[i].offsetTop<data2){
indexchild=i+1;}}
ev.target.insertBefore(document.getElementById(data),ev.target.childNodes[indexchild]);
   }
this.graph.position="absolute";
this.graph.top=ev.clientY-document.getElementById(data).offsetHeight/2-ev.target.offsetTop+ window.scrollY +"px";
this.graph.left=ev.clientX-document.getElementById(data).offsetWidth/2-ev.target.offsetLeft+window.scrollX+"px";
}


}

};
</script>
<style lang="scss">
/* CSS - Cascading Style Sheet */
/* Palette color codes */
/* Palette URL: http://paletton.com/#uid=7270u0kl1Wx1x+IcEXDsUWkWEVB */

/* Feel free to copy&paste color codes to your application */

/* As hex codes */
#div1 {
  position: absolute;
  top:20px;
    //display: flex;
//flex-direction: column;
    width: 20%;
    height: auto;
    margin: 10px;
    padding: 10px;
    border: 1px solid black;
    z-index: 2;
}
#div2 {
display: flex;
position: absolute;
top:20px;
left:22%;
    width: 70%;
    height: 1000px;
    margin: 10px;
    padding: 10px;
    border: 1px solid black;
   background-color:#fc98b7;
    z-index:0;
}
.color-primary-0 {
  color: #e1fe57;
} /* Main Primary color */
.color-primary-1 {
  color: #fdfff3;
}
.color-primary-2 {
  color: #edfe9a;
}
.color-primary-3 {
  color: #d6fe19;
}
.color-primary-4 {
  color: #d2fe00;
}

.color-secondary-1-0 {
  color: #a1fb56;
} /* Main Secondary color (1) */
.color-secondary-1-1 {
  color: #f8fff3;
}
.color-secondary-1-2 {
  color: #c6fc98;
}
.color-secondary-1-3 {
  color: #7ffb18;
}
.color-secondary-1-4 {
  color: #71fa00;
}

.color-secondary-2-0 {
  color: #fb5688;
} /* Main Secondary color (2) */
.color-secondary-2-1 {
  color: #fff3f6;
}
.color-secondary-2-2 {
  color: #fc98b7;
}
.color-secondary-2-3 {
  color: #fb185d;
}
.color-secondary-2-4 {
  color: #fa004c;
}

.color-complement-0 {
  color: #f353f3;
} /* Main Complement color */
.color-complement-1 {
  color: #fef2fe;
}
.color-complement-2 {
  color: #f695f6;
}
.color-complement-3 {
  color: #f217f2;
}
.color-complement-4 {
  color: #f000f0;
}

@font-face {
  font-family: MyFirstFont;

  src: url("SwankyandMooMoo_regular.ttf");
}

div {
  font-family: myFirstFont, Helvetica, Arial, sans-serif;
  font-size: 1em;
}

.silence {
  background-color: #c6fc98;
  width: 250px;
  height: 150px;

margin:15px;
  position: relative;
padding:10px;
  border: 1px solid rgba(0, 0, 0, 0.8);
}
.affirmation {
  background-color: #71fa00;
  width: 250px;
  height: 150px;

margin:15px;
  position: relative;
padding:10px;
  border: 1px solid rgba(0, 0, 0, 0.8);
}
.visualisation {
  background-color: #fa004c;
  width: 250px;
  height: 150px;

margin:15px;
  position: relative;
padding:10px;
  border: 1px solid rgba(0, 0, 0, 0.8);
}
.Exercice {
  background-color: #e1fe57;
  width: 250px;
  height: 150px;

margin:15px;
  position: relative;
padding:10px;
  border: 1px solid rgba(0, 0, 0, 0.8);

}
.lecture {
  background-color: #d2fe00;
  width: 250px;
  height: 150px;
margin:15px;

  position: relative;
padding:10px;
  border: 1px solid rgba(0, 0, 0, 0.8);
}
.ecrire {
  background-image: linear-gradient(to right, #fb185d, #ff007c, #ff009f, #ff00c7, #f217f2);
  width: 250px;
  height: 150px;
margin:15px;

padding:10px;
  border: 1px solid rgba(0, 0, 0, 0.8);
}

.centrage{
  position: absolute;
  top: 0;
  left: 0;

top: 50%; /* poussé de la moitié de hauteur du référent */
  transform: translateY(-50%); /* tiré de la moitié de sa propre hauteur */
 text-align: center;
}

</style>
