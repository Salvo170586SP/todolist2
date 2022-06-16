<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center py-4">
          <h1>TodolistApp</h1>
          <span class="fw-bold sp">by SalavatorePitanza</span>
        </div>
        <div class="col-12">
          <div class="input-group mb-3">
            <button
              class="btn btn-secondary"
              type="button"
              id="button-addon1"
              @click="addNote"
            >
              Aggiungi
            </button>
            <input
              type="text"
              class="form-control"
              placeholder="Aggiungi una nota"
              v-model="inputText"
              aria-label="Example text with button addon"
              aria-describedby="button-addon1"
            />
          </div>
        </div>
        <div class="col-12">
          <ul class="list-group" v-if="notes.length">
            <li
              v-for="(note, index) in notes"
              :key="index"
              class="list-group-item d-flex justify-content-between"
            >
              <span
                class="bg-light text-dark rounded"
                @click="changeDone(index)"
                :class="{ done: note.done }"
                >{{ note.text }}</span
              >
              <span role="button" @click="deleteNote(index)"
                ><i class="fa-solid fa-circle-xmark text-danger"></i
              ></span>
            </li>
          </ul>
          <div v-else class="text-center">
            <h3 class="text-center py-5">Non hai ancora nessuna nota</h3>
            <i class="fa-solid fa-calendar-plus fa-5x"></i>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      inputText: "",
      notes: [],
    };
  },
  methods: {
    addNote() {
      //se il testo del campo input non è vuoto
      if (this.inputText.trim() != "") {
        //creo un nuovo oggetto
        const newNote = {
          text: this.inputText,
          done: false,
        };
        //inserisco il nuovo oggetto nell'array
        this.notes.push(newNote);
        //svuoto il campo input
        this.inputText = "";
      }
    },
    deleteNote(index) {
      //se clicco elimino il singolo elemento
      this.notes.splice(index, 1);
    },
    changeDone(index) {
      //se clicco cambio il valore da true a false (e viceversa) per cambiare la classe del sottolineato
      this.notes[index].done = !this.notes[index].done;
    },
  },
};
</script>

<style  lang="scss">
.done {
  text-decoration: line-through;
}

h3,
i {
  color: #0000005e;
}



input:focus-visible {
  box-shadow: black 0px 0px 10px -4px;
}
.sp {
  font-size: 10px;
}
</style>