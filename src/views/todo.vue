<template>
  <div>
    <div class="container">
      <center>
        <div>
          <h1>DAFTAR AGENDA KULIAH</h1>

          <form @submit.prevent="addAgendaItem">
            <input type="text" v-model="newAgenda" placeholder="Tambahkan agenda baru" />
            <button type="submit">Tambah</button>
          </form>
          <table>
            <thead>
              <tr>
                <th style="text-align: center">Agenda</th>
                <th style="text-align: center">Batalkan</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(agenda, index) in filteredAgendaItems" :key="index" :class="{ completed: completedItems.includes(index) && showAll }">
                <td>
                  <input type="checkbox" v-if="showAll" v-bind:checked="completedItems.includes(index)" @change="toggleComplete(index)" />
                  <span v-bind:class="{ completed: completedItems.includes(index) && showAll }">{{ agenda }}</span>
                </td>
                <td>
                  <button @click="cancelAgendaItem(index)">Batalkan</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <div>
          <button @click="showAll = true">Tampilkan Semua</button>
          <button @click="showAll = false">Belum Selesai</button>
        </div>
        <p>NB: Pastikan untuk menekan tombol "Semua" agar dapat kembali memilih Agenda untuk diselesaikan</p>
      </center>
    </div>
    <div class="blur"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      agendaItems: ["Bukber Angkatan (19 April)", "Makalah Mat. Diskrit", "PPT Basis Data"],
      newAgenda: "",
      completedItems: [],
      showAll: true,
    };
  },
  computed: {
    filteredAgendaItems() {
      if (this.showAll) {
        return this.agendaItems;
      } else {
        return this.agendaItems.filter((_, index) => !this.completedItems.includes(index));
      }
    },
  },
  methods: {
    addAgendaItem() {
      if (this.newAgenda.trim() !== "") {
        this.agendaItems.push(this.newAgenda.trim());
        this.newAgenda = "";
      }
    },
    cancelAgendaItem(index) {
      this.agendaItems.splice(index, 1);
      this.completedItems = this.completedItems.filter((i) => i !== index);
    },
    toggleComplete(index) {
      if (this.completedItems.includes(index)) {
        this.completedItems = this.completedItems.filter((i) => i !== index);
      } else {
        this.completedItems.push(index);
      }
    },
  },
};
</script>

<style>
.container {
  width: 80%;
  margin: 0 auto;
}

table {
  width: 100%;
  border-collapse: collapse;
}

table th,
table td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

table th {
  background-color: #f2f2f2;
}

.completed {
  text-decoration: line-through;
  color: #999;
}

form {
  margin-bottom: 16px;
}

button {
  padding: 8px 16px;
  background-color: #4caf50;
  color: white;
  border: none;
  cursor: pointer;
}


</style>
