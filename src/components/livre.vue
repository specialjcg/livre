<template>
<div>

<div id="div1" @drop.self="drop($event)" @dragover="allowDrop($event)">

 <div class="silence" draggable="true" @dragstart="drag($event)" id="drag1" :style="graph" >

 <div class="centrage">
      <b> Silence :</b> il s’agit de maitriser notre conscience et réduire notre stress en méditant, priant, respirant, réfléchissant…
   </div>
</div>
 <div class="affirmation" draggable="true" @dragstart="drag($event)" id="drag2" :style="graph">
<div class="centrage">
<b>Affirmation :</b> il faut répéter à voix haute, écrire, imaginer, des affirmations sur la personne que nous voulons devenir

   </div>
   </div>
 <div class="visualisation" draggable="true" @dragstart="drag($event)" id="drag3" :style="graph" >
<div class="centrage">
<b>Visualisation :</b>
 cela consiste à imaginer ce que nous voulons devenir et de nous imaginer en train de l’accomplir

   </div>
   </div>
 <div class="Exercice" draggable="true" @dragstart="drag($event)" id="drag4" :style="graph" >
<div class="centrage">
<b>Exercice :</b> non il ne s’agit pas d’exercice de mathématique mais bien d’exercice physique, de sport, de se bouger les fesses, que ce soit en marchant, en courant, en faisant des exercices chez soi ou en allant dans une salle de sport

   </div>
   </div>
 <div class="lecture" draggable="true" @dragstart="drag($event)" id="drag5" :style="graph">
<div class="centrage">

<b>Lecture :</b> afin d’acquérir des connaissances Hal recommande de lire chaque matin quelques pages d’un livre de non fiction

</div></div>
 <div class="ecrire"  draggable="true" @dragstart="drag($event)" id="drag6" :style="graph">

<div class="centrage">
<b>Ecrire :</b> tenir un journal et y écrire chaque matin nos idées, nos projets, ce pourquoi nous sommes reconnaissant, ce qui nous rends heureux

</div></div>

</div>
<div id="div2" @drop.self="drop($event)" @dragover="allowDrop($event)"></div>

   </div>

</template>
<script>
export default {
  data () {
    return {
      avant: true,
      graph: {
        position: 'relative',
        top: 0,
        left: 0

      }
    }
  },
  computed: {
    computed_class () {
      if (this.avant) {
        return { avant: this.avant }
      } else {
        return { après: !this.avant }
      }
    }},

  methods: {
    allowDrop (ev) {
      ev.preventDefault()
    },

    drag (ev) {
      ev.dataTransfer.setData('text', ev.target.id)
    },
    drop (ev) {
      ev.preventDefault()

      var indexchild = 0
      var data = ev.dataTransfer.getData('text')
      var data2 = ev.clientY
      if (ev.target.id === 'div2') {
        ev.target.appendChild(document.getElementById(data))

        document.getElementById(data).style.position = 'absolute'
        document.getElementById(data).style.top = ev.clientY - document.getElementById(data).offsetHeight / 2 - ev.target.offsetTop + window.scrollY + 'px'
        document.getElementById(data).style.left = ev.clientX - document.getElementById(data).offsetWidth / 2 - ev.target.offsetLeft + window.scrollX + 'px'
        document.getElementById(data).classList.remove('expen')
        document.getElementById(data).classList.toggle('expen')
      } else {
        if (ev.target.children.length === 0) {
          ev.target.insertBefore(document.getElementById(data), ev.target.firstChild)
          document.getElementById(data).style.position = 'relative'
          document.getElementById(data).style.top = 0
          document.getElementById(data).style.left = 0
          document.getElementById(data).classList.remove('expen')
          document.getElementById(data).classList.toggle('expen')
        } else {
          for (var i = 0; i < ev.target.children.length; i++) {
            if (ev.target.children[i].offsetTop < (data2 - 25 + window.scrollY)) {
              indexchild = i + 1
            }
          }
          ev.target.insertBefore(document.getElementById(data), ev.target.children[indexchild])
          document.getElementById(data).style.position = 'relative'
          document.getElementById(data).style.top = 0
          document.getElementById(data).style.left = 0
          document.getElementById(data).classList.remove('expen')
          document.getElementById(data).classList.toggle('expen')
        }
      }
    }

  }

}
</script>
<style lang="scss">
/* CSS - Cascading Style Sheet */
/* Palette color codes */
/* Palette URL: http://paletton.com/#uid=7270u0kl1Wx1x+IcEXDsUWkWEVB */

/* Feel free to copy&paste color codes to your application */

/* As hex codes */
#div1 {
  background-image: linear-gradient(to bottom, #ead5db, #f0d8d4, #efdccf, #e8e3cf, #dee9d5);
  position: absolute;
  top:20px;
    //display: flex;
//flex-direction: column;
    width: 20%;
    height: 1200px;

    margin: 10px;
    padding: 10px;
    border: 1px solid black;
    z-index: 2;
}
#div2 {
//display: flex;
position: absolute;
top:20px;
left:22%;
    width: 70%;
    height: 1200px;
    margin: 10px;
    padding: 10px;
    border: 1px solid black;
  background-image: linear-gradient(to bottom, #90008a, #9d4197, #a867a4, #b289b0, #bcabbb);
    z-index:0;
}

@font-face {
  font-family: MyFirstFont;

  src: url("Montaga_regular.ttf");
}

div {
  font-family: myFirstFont, Helvetica, Arial, sans-serif;
  font-size: 1em;
}
/* Main Primary color */
.color-primary-0 { color: #FA004C }
.color-primary-1 { color: #EAD5DB }
.color-primary-2 { color: #F35686 }
.color-primary-3 { color: #F4004A }
.color-primary-4 { color: #C2003B }
/* Main Secondary color (1) */
.color-secondary-1-0 { color: #FF4500 }
.color-secondary-1-1 { color: #FFEFE9 }
.color-secondary-1-2 { color: #FF875A }
.color-secondary-1-3 { color: #FF4500 }
.color-secondary-1-4 { color: #D93B00 }
/* Main Secondary color (2) */
.color-secondary-2-0 { color: #EF00E5 }
.color-secondary-2-1 { color: #BCABBB }
.color-secondary-2-2 { color: #DA4DD3 }
.color-secondary-2-3 { color: #DD00D3 }
.color-secondary-2-4 { color: #90008A }
/* Main Complement color */
.color-complement-0 { color: #71FA00 }
.color-complement-1 { color: #DEE9D5 }
.color-complement-2 { color: #9DF356 }
.color-complement-3 { color: #6FF400 }
.color-complement-4 { color: #58C100 }
.silence {
  background-image: linear-gradient(to right, #d93b00, #e3501d, #ed6332, #f67546, #ff875a);
  width: 250px;
  height: 150px;

margin:15px;
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 255, .2);
  border-radius: 50% 20% / 10% 40%;
padding:10px;
  border: 1px solid #d93b00;
}
.affirmation {
 background-image: linear-gradient(to right top, #58c100, #80cc4e, #a2d67d, #c1e0a9, #dee9d5);
  width: 250px;
  height: 150px;
box-shadow: 2px 2px 2px 1px rgba(0, 0, 255, .2);
  border-radius: 50% 20% / 10% 40%;
margin:15px;

padding:10px;
  border: 1px solid #58c100;
}
.visualisation {
  background-image: linear-gradient(to right, #fa004c, #fc245c, #fc386b, #fc487a, #fb5688);
  width: 250px;
  height: 150px;

margin:15px;
box-shadow: 2px 2px 2px 1px rgba(0, 0, 255, .2);
  border-radius: 50% 20% / 10% 40%;
padding:10px;
  border: 1px solid #fa004c;
}
.Exercice {
  background-image: linear-gradient(to right, #71fa00, #7ffa26, #8bfb39, #97fb48, #a1fb56);
  width: 250px;
  height: 150px;
box-shadow: 2px 2px 2px 1px rgba(0, 0, 255, .2);
  border-radius: 50% 20% / 10% 40%;
margin:15px;

padding:10px;
  border: 1px solid #71fa00;

}
.lecture {
 background-image: linear-gradient(to right, #d2fe00, #d6fe27, #dafe3b, #defe4a, #e1fe57);
  width: 250px;
  height: 150px;
margin:15px;
box-shadow: 2px 2px 2px 1px rgba(0, 0, 255, .2);
  border-radius: 50% 20% / 10% 40%;

padding:10px;
  border: 1px solid #d2fe00;
}
.ecrire {
  background-image: linear-gradient(to right, #fb185d, #ff007c, #ff009f, #ff00c7, #f217f2);
  width: 250px;
  height: 150px;
margin:15px;
box-shadow: 2px 2px 2px 1px rgba(0, 0, 255, .2);
  border-radius: 50% 20% / 10% 40%;
padding:10px;
  border: 1px solid #fb185d;
}

.centrage{
  position: absolute;
  top: 0;
  left: 0;

top: 50%; /* poussé de la moitié de hauteur du référent */
  transform: translateY(-50%); /* tiré de la moitié de sa propre hauteur */
 text-align: center;
}
.expen
{
 animation-duration: 1s;
  animation-name: boom;

}
@keyframes boom
{
0% {
  transform:  scale(1);
  opacity: 1;
  }
50% {
  transform:  scale(1.2);
  opacity: 0.5;}
100%{
  transform: scale(1);
  opacity: 1;}
}
</style>
