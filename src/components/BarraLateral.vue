<template>

  <header class="menu">
    <h1>
      <img src="../assets/logo.png" alt="" />
    </h1>
    <div class="has-text-centered">
    <button class="button" @click="alterarTema">{{ textoBotao }}</button>
    </div>
    <nav class="panel mt-5">
      <ul>
        <li>
          <router-link to="/" class="link">
            <i class="fas fa-tasks">
              Tarefas
            </i>
          </router-link>
        </li>
        <li>
          <router-link to="/projetos" class="link">
            <i class="fas fa-project-diagram">
              Projetos
            </i>
          </router-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BarraLateral",
  emits: ["aoTemaAlterado"],
  data: () => {
    return {
      modoEscuroAtivo: false,
    };
  },
  computed: {
    textoBotao() {
      if (this.modoEscuroAtivo) {
        return "Desativar modo escuro";
      }
      return "Ativar modo escuro";
    },
  },
  methods: {
    alterarTema() {
      this.modoEscuroAtivo = !this.modoEscuroAtivo;
      this.$emit("aoTemaAlterado", this.modoEscuroAtivo);
    },
  },
});
</script>

<style scoped>
header {
  padding: 1rem;
  width: 100%;
  height: 100vh;
  text-align: center;
  color: var(--texto-primario);
  background-color: var(--barra-lateral);
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
.panel li {
  margin: 8px 0;
}
.link {
  color: var(--texto-primario);
  background-color: var(--barra-lateral);
}
.link:hover {
  color: var(--texto-primario);
  background-color: var(--barra-lateral);
}
.link.router-link-active {
  color: #FAF0CA;
}
</style>
