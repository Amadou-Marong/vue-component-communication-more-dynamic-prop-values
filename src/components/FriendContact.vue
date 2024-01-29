<template>
  <li>
    <h2>{{ name }} {{friendIsFavourite ? '(Favourite)' : ''}}</h2>
    <button @click="toggleFavorite">{{ friendIsFavourite ? 'Remove from favourites' : 'Add to favourites' }}</button>
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
      type: Boolean,
      required: false,
      default: false,   // can also be a function that returns the default value
      // validator: function(value) {     // validator is a function that returns true or false if the value is valid or not
      //   return value === '0' || value === '1';
      // }
    } 
  },
  data() {
    return {
      detailsAreVisible: false,
      friendIsFavourite: this.isFavorite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.friendIsFavourite = !this.friendIsFavourite;
    }
  }
};
</script>