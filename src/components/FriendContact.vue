<template>
  <li>
    <h2>{{ name }} {{friendIsFavourite === '1' ? '(Favourite)' : ''}}</h2>
    <button @click="toggleFavorite">{{ friendIsFavourite ==='1' ? 'Remove from favourites' : 'Add to favourites' }}</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  // props: ['name', 'phoneNumber', 'emailAddress', 'isFavorite'],
  // props: {name: String, phoneNumber: String, emailAddress: String, isFavorite: String,},
  props: {
    name: {
      type: String,
      required: true
    },
    phoneNumber: {
      type: String,
      required: true
    },
    emailAddress: {
      type: String,
      required: true
    },
    isFavorite: {
      type: String,
      required: false,
      default: '0',   // can also be a function that returns the default value
      validator: function(value) {     // validator is a function that returns true or false if the value is valid or not
        return value === '0' || value === '1';
      }
    } 
  },
  data() {
    return {
      detailsAreVisible: false,
      friend: {
        id: "manuel",
        name: "Manuel Lorenz",
        phone: "0123 45678 90",
        email: "manuel@localhost.com",
      },
      friendIsFavourite: this.isFavorite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      if (this.friendIsFavourite === '1'){
        this.friendIsFavourite = '0';
      }else{
        this.friendIsFavourite = '1';
      }  
    }
  }
};
</script>