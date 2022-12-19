<template>
  <!-- Portfolio Section -->
  <section class="page-section">
    <b-container>
      <HeaderPage title="Adicionar Especialista" />

      <!--FORM-->
      <b-row>
        <b-col cols="2"></b-col>
        <b-col>
          <form @submit.prevent="add">
            <div class="form-group">
              <input
                v-model="name"
                type="text"
                class="form-control form-control-lg"
                id="txtName"
                placeholder="escreve nome"
                required
              />
            </div>
            <div class="form-group">
              <input
                id="txtProfissao"
                class="form-control form-control-lg"
                placeholder="escreve profissão"
                v-model="description"
                required/>
            </div>
            <div class="form-group">
              <input
                  id="txtAnosExperiencia"
                  class="form-control form-control-lg"
                  placeholder="anos de experiencia"
                  type="number"
                  required/>
            </div>
            <button type="submit" class="btn btn-outline-success btn-lg mr-2">
              <i class="fas fa-plus-square"></i>  ADICIONAR</button>
            <router-link
              :to="{name: 'listExperts'}"
              tag="button"
              class="btn btn-outline-danger btn-lg"
            ><i class="fas fa-window-close"></i>  CANCELAR</router-link>
          </form>
        </b-col>
        <b-col cols="2"></b-col>
      </b-row>
    </b-container>
  </section>
</template>

<script>
import { ADD_ANIMAL } from "@/store/animals/animal.constants";
import HeaderPage from "@/components/HeaderPage.vue";
import router from "@/router";
import { mapGetters } from "vuex";

export default {
  name: "AddAnimal",
  components: {
    HeaderPage
  },
  data: () => {
    return {
      name: "",
      group: "",
      description: "",
      level: "",
      links: [
        { types: "photo", url: "" },
        { types: "video", url: "" },
        { types: "sound", url: "" }
      ],
      evaluation: [],
      comments: []
    };
  },
  computed: {
    ...mapGetters("animal", ["getMessage"])
  },
  methods: {
    add() {
      this.$store.dispatch(`animal/${ADD_ANIMAL}`, this.$data).then(
        () => {
          this.$alert(this.getMessage, "Animal adicionado!", "success");
          router.push({ name: "listAnimals" });
        },
        err => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    }
  }
};
</script>
