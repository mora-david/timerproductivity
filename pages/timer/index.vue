<template>
    <div>

        <div class="fat">
        <div class="maincont">
        <h2 v->Working</h2>
        <div style="font-size: 1.3rem">{{Math.trunc(date/60)}} minutos</div>
        <div style="font-size: 1.3rem">{{Math.trunc(((date/60)/totaltime)*100)}} %</div>
          <div class="button-group">
        <div><button v-if="s1==0" @click="refreshw(), disapir()">Iniciar</button></div>
        <div><button v-if="stop=='parar'" @click="continuesw()">Continue</button></div>
        <div><button v-if="stop=='no'" @click="stopitw()">Parar</button></div>
          </div>
        </div>


        <div class="maincont">
        <h2 v->Lazy</h2>
        <div style="font-size: 1.3rem">{{Math.trunc(datel/60)}} minutos</div>
        <div style="font-size: 1.3rem">{{Math.trunc(((datel/60)/totaltime)*100)}} %</div>
          <div class="button-group">
        <div><button v-if="s2==0" @click="refreshl(),disapir2()">Iniciar</button></div>
        <div><button v-if="stopl=='parar'" @click="continuesl()">Continue</button></div>
        <div><button v-if="stopl=='no'" @click="stopitl()">Parar</button></div>
            </div>
        </div>

        <div class="maincont">
        <h2 v->Resting</h2>
        <div style="font-size: 1.3rem">{{Math.trunc(dater/60)}} minutos</div>
        <div style="font-size: 1.3rem">{{Math.trunc(((dater/60)/totaltime)*100)}} %</div>

          <div class="button-group">
        <div><button v-if="s3==0" @click="refreshr(),disapir3()">Iniciar</button></div>
        <div><button v-if="stopr=='parar'"@click="continuesr()">Continue</button></div>
        <div><button v-if="stopr=='no'" @click="stopitr()">Parar</button></div>
            </div>
        </div>


        </div>
<diV class= "maincont">
<h2>Total time</h2>
        <div style="font-size: 1.3rem">{{this.totaltime-60*totaltimeh}} minutos</div>
        <div style="font-size: 1.3rem"v-if="totaltimeh>0">{{this.totaltimeh}} horas</div>
</div>
    </div>
</template>




<script>

export default {
  data(){
    return{
        s1:0,
        s2:0,
        s3:0,
        date:0,
        stop: 'no',

        datel:0,
        stopl:'no',

        dater:0,
        stopr:'no',


        totaltime:0,
        totaltimeh: 0


  }},
  created(){
      //this.refresh()

      this.totaltimer()

  },
  mounted(){
  },
  methods:{

      disapir(){
          this.s1=1
      },
      disapir2(){
          this.s2=1
      },
      disapir3(){
          this.s3=1
      },

      totaltimer(){

//this.stopitr()
//this.stopitl()

          let b = this.date + this.datel + this.dater

          if(b > 60){
              this.totaltime = Math.trunc(b/60)
              if(b > 3600){
                  this.totaltimeh = Math.trunc(b/3600)
              }
          }

            else{
                this.totaltime = 0
            }


          let a = setTimeout(this.totaltimer, 1000)
      },



    refreshw(){
        if(this.stop==='parar'){

        }


else{

    this.date = this.date + 1

            let a = setTimeout(this.refreshw, 1000)
}

},

stopitw(){
   this.stop = 'parar'
},
continuesw(){
    this.stop = 'no'
    let a = this.refreshw()


},

refreshl(){
        if(this.stopl==='parar'){

        }


else{

    this.datel = this.datel + 1

            let a = setTimeout(this.refreshl, 1000)
}

},

stopitl(){
   this.stopl = 'parar'
},
continuesl(){
    this.stopl = 'no'
    let a = this.refreshl()


},






refreshr(){
        if(this.stopr==='parar'){

        }


else{

    this.dater = this.dater + 1

            let a = setTimeout(this.refreshr, 1000)
}

},

stopitr(){
   this.stopr = 'parar'
},
continuesr(){
    this.stopr = 'no'
    let a = this.refreshr()
},



},
components:{

}

}
</script>


<style>
  body{
    background: darkslategray;
    color: blanchedalmond;
  }


.maincont{
    padding:30px;
    padding-bottom: 10px;
}



.fat{
    display: flex;
}

.button-group button{
  width: 100px;
  }






</style>
