<template>
  <li>
    <!-- <h2>{{ name }} {{friendIsFavourite ? '(Favourite)' : ''}}</h2> -->
    <h2>{{ name }} {{isFavorite ? '(Favorite)' : ''}}</h2>
    <button @click="toggleFavorite">{{ isFavorite ? 'Remove from favourites' : 'Add to favourites' }}</button>
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
    id: {
      type: String,
      required: true
    },
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
    } 
  },
  data() {
    return {
      detailsAreVisible: false,
      // friendIsFavourite: this.isFavorite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit('toggle-favorite', this.id);
    }
  }
};
</script>