<script>
    export default { 
        // Add code in appropriate places
        data() {
            return {
                items: ['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'],
                newItem: ''
            }
            
        },
        methods:{
            addItem(){
                //add new item to item array
                this.items.push(this.newItem);
            }
        }
    }
</script>

<template>

    <h2>Shopping Cart</h2>
    <ul id="items">
        <li v-for="(item, idx) in items">
           {{ item }}
           <button @click="items.splice(idx, 1)">Delete!</button>
        </li>
    </ul>
        <input type = "text" v-model="newItem">
        <button @click="addItem">Add!</button>

    

</template>
