<template>
    <li>
        <h2>{{ name }} {{ isFavourite ? "(Favourite)" : "" }}</h2>
        <button @click="toggleDetails">
            {{ detailsAreVisible ? "Hide" : "Show" }} Details
        </button>
        <button @click="toggleFavourite">Toggle Favourite</button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone:</strong>{{ phoneNumber }}</li>
            <li><strong>Email:</strong>{{ emailAddress }}</li>
        </ul>
        <button @click="$emit('delete', id)">Delete</button>
    </li>
</template>

<script>
export default {
    //   props: [
    //     'name',
    //     'phoneNumber',
    //     'emailAddress',
    //     'isFavourite'
    //   ],
    props: {
        id: {
            type: String,
        },
        name: {
            type: String,
            required: true,
        },
        phoneNumber: {
            type: String,
            required: true,
        },
        emailAddress: {
            type: String,
            required: true,
        },
        isFavourite: {
            type: Boolean,
            required: false,
            default: false,
            // validator: function(value) {
            //     return value === '1' || value === '0';
            // }
        },
    },
    // You can use a list too - ['toggle-fav']
    emits: ["toggle-favourite", "delete"], 
    // {
    //     "toggle-favourite": function (id) {
    //         if (id) return true;
    //         else {
    //             console.warn("ID is missing");
    //             return false;
    //         }
    //     },
    // },
    data() {
        return {
            detailsAreVisible: false,
            // friend: {
            //     name: this.name,
            //     phone: this.phoneNumber,
            //     email: this.emailAddress
            // },
            // friendIsFavourite: this.isFavourite,
        };
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavourite() {
            // if (this.friendIsFavourite === '1') this.friendIsFavourite = '0';
            // else this.friendIsFavourite = '1';
            // this.friendIsFavourite = !this.friendIsFavourite;
            // this.$emit('toggle-favourite', this.isFavourite);
            this.$emit("toggle-favourite", this.id);
        },
    },
};
</script>
