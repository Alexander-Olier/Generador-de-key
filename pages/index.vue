 <template>
  <v-container>
    <h1>Lista de citas</h1>
    <v-row>
      <v-col class="col-8">
        <ul v-for="(item, index) in listCitas" :key="index">
          <li style="font-size: 20px">{{ item.cita }}</li>
        </ul>
      </v-col>
      <v-col class="col-4">
        <v-btn rounded color="blue" @click="addCod">Solicitar cita</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      listCitas: [{ cita: "A1" }, { cita: "A2" }, { cita: "B1" }],
      cod: "",
    };
  },
  methods: {
    randomCode() {
      let Rlet = Math.floor(Math.random() * (4 - 0 + 0) + 0);
      let Rnum = Math.floor(Math.random() * (100 - 0 + 0) + 0);
      let letras = ["A", "B", "C", "D"];
      let ltrs = letras[Rlet];
      return ltrs + Rnum;
    },
    verificarCode() {
      let codigoFinal = null;
      let cod = this.randomCode();
      console.log(cod);
      while (codigoFinal == null) {
        if (this.listCitas.find((e) => e.cita !== cod)) {
          codigoFinal = { cita: cod };
        }
      }
      return codigoFinal;
    },
    addCod() {
      this.listCitas.push(this.verificarCode());
    },
  },
};
</script>
