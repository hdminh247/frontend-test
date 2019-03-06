<template>
  <div class="container">
  <div class="food-order-title">
    Please enter your food info
  </div>
  <form>
    <div class="field">
      <label class="label">Name</label>
      <div class="control">
        <input class="input col-is-4" type="text" v-model="foodName" placeholder="Enter your food name" required/>
      </div>
    </div>
    <div class="field">
      <label class="label">Quantity</label>
      <div class="control">
        <input class="input col-is-4" type="number" v-model="foodQuantity" placeholder="Enter food quantity" required/>
      </div>
    </div>
  <div class="field">
    <div class="control">
      <button class="button is-success" @click.prevent="addFood">Add</button>
    </div>
  </div>
</form>

<div class="food-list-title">
  Food list
</div>

<table v-if="foodList.length > 0" class="table is-striped">
  <tr>
    <th>Food</th>
    <th>Quantity</th>
    <th>Action</th>
  </tr>
  <tr v-for="(item, index) in foodList">
    <td>{{ item.name }}</td>
    <td>{{ item.quantity }}</td>
    <td>
      <button @click="editFoodItem(index)" class="button is-success">Edit</button>
      <button @click="deleteData(index)" class="button is-danger">Delete</button>
    </td>
  </tr>
</table>


<EditModal :editData="editData" v-if="showEditModal" @close="hideEditModal"></EditModal>

</div>
</template>
<script>
import EditModal from './EditModal.vue';

// Save data to local storage
const backupData = (data) => {
    console.log(data)
    localStorage.setItem('foodList', JSON.stringify(data));
};

// Get data from local storage
const getBackupData = () => {
    return localStorage.getItem('foodList') ? JSON.parse(localStorage.getItem('foodList')) : null;
};

export default {
  mounted: function() {
      let backupData = getBackupData();
      this.foodList = backupData ? backupData: [];
  },
  data: function(){
    return {
        foodName: '',
        foodQuantity: '',
        foodList: [],
        showEditModal: false,
        editData: {
            index: 0,
            foodName: '',
            foodQuantity: ''
        }
    }
  },
  components: {
      EditModal
  },
  methods: {
      addFood(){
        if(this.foodName !== '' && this.foodQuantity !== ''){
            // Add food item to foodList
            this.foodList.push({name: this.foodName, quantity: this.foodQuantity});

            // Reset value
            this.foodName = '';
            this.foodQuantity = '';

            // Backup data
            backupData(this.foodList)
        }
    },

    // Delete food item at specific index
    deleteData(index){
      this.foodList.splice(index, 1);

        // Backup data
        backupData(this.foodList)
    },

    // Open edit modal to edit food item
    editFoodItem(index){
      // Value to edit
      this.editData.index = index;
      this.editData.foodName = this.foodList[index].name;
      this.editData.foodQuantity = this.foodList[index].quantity;

      // Show edit modal
      this.showEditModal = true;

        // Backup data
        backupData(this.foodList)
    },

    // Hide edit modal
    hideEditModal(value){
      // Edit current data
      if(value){
          this.foodList[value.index].name = value.name;
          this.foodList[value.index].quantity = value.quantity

          // Backup data
          backupData(this.foodList)
      }
      // Hide edit modal
      this.showEditModal = false;
    }
  }
}
</script>
