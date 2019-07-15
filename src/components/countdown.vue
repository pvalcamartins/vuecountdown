<template>
  <div class="box">
    <div class="box-counter">
      <div>
        <span>{{ showDd }}</span>
        <span class="texto">{{ diaDias }}</span>
      </div>
      <div>
        <span>{{ showHh }}</span>
        <span class="texto">{{ horaHoras }}</span>
      </div>
      <div>
        <span>{{ showMi }}</span>
        <span class="texto">{{ minutoMinutos }}</span>
      </div>
      <div>
        <span>{{ showSs }}</span>
        <span class="texto">{{ segundoSegundos }}</span>
      </div>
    </div>
    <div>
      <span class="chegou">{{ chegou }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "CountDown",
  data() {
    return {
      YY: 2020,
      MM: 7,
      DD: 15,
      HH: 23,
      MI: 59,
      SS: 59,
      showDd: "",
      showHh: "",
      showMi: "",
      showSs: "",
      diaDias: "",
      horaHoras: "",
      minutoMinutos: "",
      segundoSegundos: "",
      chegou: ""
    };
  },
  methods: {
    atualizaContador: function() {
      var hoje = new Date();
      var futuro = new Date(
        this.YY,
        this.MM - 1,
        this.DD,
        this.HH,
        this.MI,
        this.SS
      );
      var ss = parseInt((futuro - hoje) / 1000);
      var mm = parseInt(ss / 60);
      var hh = parseInt(mm / 60);
      var dd = parseInt(hh / 24);
      ss = ss - mm * 60;
      mm = mm - hh * 60;
      hh = hh - dd * 24;

      var dias = toString(dd).length ? dd : "";
      var diaOuDias = dd && dd > 1 ? "dias" : "dia";
      var horas = toString(hh).length ? hh : "";
      var horaOuHoras = hh && hh > 1 ? "horas" : "hora";
      var minutos = toString(mm).length ? mm : "";
      var minutoOuMinutos = mm && mm > 1 ? "minutos" : "minuto";
      var segundos = ss;
      var segundoOuSegundos = ss && ss > 1 ? "segundos" : "segundo";
      if (dd + hh + mm + ss > 0) {
        this.showDd = dias;
        this.diaDias = diaOuDias;
        this.showHh = horas;
        this.horaHoras = horaOuHoras;
        this.showMi = minutos;
        this.minutoMinutos = minutoOuMinutos;
        this.showSs = segundos;
        this.segundoSegundos = segundoOuSegundos;
        setTimeout(this.atualizaContador, 1000);
      } else {
        console.log("CHEGOU");
        this.chegou = "CHEGOU";
      }
    }
  },
  created() {
    this.atualizaContador();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div.box {
  display: flex;
  width: 100%;
  height: 100%;
  position: relative;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  flex-wrap: wrap;
}
div.box-counter {
  width: 100%;
  height: 70%;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  padding: 40px 0 40px 0;
}
div.box-counter div {
  font-size: 7vw;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
  color: #42b983;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
div.box-counter div span.texto {
  font-size: 1.5vw;
  font-weight: 400;
  color: #808080;
}
div span.chegou{
  font-size: 7vw;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
  color: #42b983;
}
</style>
