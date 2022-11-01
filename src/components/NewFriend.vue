<template>
    <form @submit.prevent="submitData">
        <div>
            <label>Name</label>
            <input type="text" name="" id="" v-model="enteredName" />
        </div>
        <div>
            <label>Phone</label>
            <input type="tel" name="" id="" v-model="enteredPhone" />
        </div>
        <div>
            <label>E-mail</label>
            <input type="email" name="" id="" v-model="enteredEmail" />
        </div>
        <div>
            <button>Add Contact</button>
        </div>
    </form>
</template>

<script>
export default {
    emits: ["add-contact"],
    data() {
        return {
            enteredName: "",
            enteredPhone: "",
            enteredEmail: "",
        };
    },
    methods: {
        submitData() {
            this.$emit(
                "add-contact",
                this.enteredName,
                this.enteredPhone,
                this.enteredEmail
            );
            // Clear input after submitting
            this.enteredName = "";
            this.enteredPhone = "";
            this.enteredEmail = "";
        },
    },
};
</script>
