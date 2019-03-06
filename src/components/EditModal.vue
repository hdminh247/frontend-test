<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">

          <div class="modal-header">
            <slot name="header">
              Edit Food
            </slot>
          </div>

          <div class="modal-body">
            <slot name="body">
              <form>
                <div class="field">
                  <label class="label">Name</label>
                  <div class="control">
                    <input class="input col-is-4" type="text" v-model="foodName" placeholder="Enter your food name"/>
                  </div>
                </div>
                <div class="field">
                  <label class="label">Quantity</label>
                  <div class="control">
                    <input class="input col-is-4" type="number" v-model="foodQuantity" placeholder="Enter food quantity"/>
                  </div>
                </div>
                <div class="field">
                  <div class="control">
                    <button class="button is-success" @click.prevent="onSubmit">Confirm</button>
                    <button class="button is-danger" @click.prevent="onClose">Cancel</button>
                  </div>
                </div>
              </form>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>


<script>
export default {
  props: ['editData'],
  data: function(){
    return {
        index: this.editData.index,
        foodName: this.editData.foodName,
        foodQuantity: this.editData.foodQuantity,
    }
  },
  methods: {
      onSubmit(){
          this.$emit('close', {index: this.index, name: this.foodName, quantity: this.foodQuantity})
      },
      onClose(){
          this.$emit('close',null)
      }
  }
}
</script>
