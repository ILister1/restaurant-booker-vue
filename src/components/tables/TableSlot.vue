<template>
    <div class="table">
        <p class="table_num">{{ table.id }}</p> 
        <input v-if="edit" class="seats_form" type="text" v-model="seats" :placeholder="table.number_of_seats">
        <p v-else class="num_seats">{{ table.number_of_seats }}</p>
        <button class="update" v-if="!edit" v-on:click="edit = !edit">&#9998;</button>
        <button class="updating" v-else v-on:click="edit = !edit; this.seats = '';">&#9998;</button>
        <button class="del" v-if="!edit" v-on:click="delTable">X</button>
        <button class="edit" v-else v-on:click="editTable">	&#10004;</button>
    </div>
</template>

<script>
export default {
    name: "TableSlot",
    props: ["table"],
    data() {
        return {
            edit: false,
            seats: ''
        }
    },
    methods: {
        delTable() {
            this.$emit('del-table', this.table.id)
        },
        editTable() {
            const updatedTable = {
                id: this.table.id,
                number_of_seats: Number(this.seats)
            }
            this.$emit('edit-table', updatedTable)
            this.edit = false
            this.seats = ''

        }
    }
}
</script>

<style scoped>
.table {
    background: #f4f4f4;
    padding: 1px;
    border-bottom: 1px #ccc dotted;
    text-align: center;
    overflow: hidden;
  }
.table_num {
    width: 50%;
    float: left;
}
.num_seats {
    width: 50%;
    float: right;
}
@media (max-width: 800px) {
input {
    width: 22%;
    padding: 10px;
    text-align: center;
    font-size: 1pc;
    margin-left: 10%;
    margin-right: 8%;
}
.update {
    background: blue;
    color: #000000;
    border: none;
    padding: 5px 7px;
    cursor: pointer;
    float: left;
    margin: -10% 1%;
  }
.del {
    background: #ff0000;
    color: #000000;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: right;
    position: relative;
    margin: -10% 1%;
  }
.edit {
    background: #71EA6B;
    color: #000000;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: right;
    margin: -9% 1%;
  }
.updating {
    background: blue;
    color: #000000;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: left;
    margin: -9% -5%;
  }
}
@media (min-width: 801px) {
input {
    width: 22%;
    padding: 10px;
    text-align: center;
    font-size: 1pc;
    margin-left: 10%;
    margin-right: 6%;
}
.del {
    background: #ff0000;
    color: #000000;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: right;
    position: relative;
    margin: -2.5% 1%;
  }
.edit {
    background: #71EA6B;
    color: #000000;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: right;
    margin: 1% 1%;
  }
.update {
    background: blue;
    color: #000000;
    border: none;
    padding: 5px 7px;
    cursor: pointer;
    float: left;
    margin: -2.5% 1%;
  }
.updating {
    background: blue;
    color: #000000;
    border: none;
    padding: 5px 7px;
    cursor: pointer;
    float: left;
    margin: 1% -49%;
  }
}
</style>