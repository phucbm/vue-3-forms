<template>
  <div>
    <h1>Create an event</h1>
    <p>Fill in the form, press submit, then open the console log to see response data.</p>
    <form @submit.prevent="sendForm">

      <fieldset>
        <legend>Name & describe your event</legend>
        <BaseSelect
            :options="categories"
            v-model="event.category"
            label="Select a category"
        />
        <BaseInput
            v-model="event.title"
            label="Title"
            type="text"
            error="Oops! There's something wrong."
        />
        <BaseInput
            v-model="event.description"
            label="Description"
            type="text"
        />
      </fieldset>

      <fieldset>
        <legend>Where is your event?</legend>
        <BaseInput
            v-model="event.location"
            label="Location"
            type="text"
        />
      </fieldset>

      <fieldset>
        <legend>Are pets allowed?</legend>
        <div>
          <BaseRadioGroup
              v-model="event.pets"
              name="pets"
              :options="petOptions"
          />
        </div>
      </fieldset>

      <fieldset>
        <legend>Extras</legend>
        <div>
          <BaseCheckbox
              v-model="event.extras.catering"
              label="Catering"
          />
        </div>
        <div>
          <BaseCheckbox
              v-model="event.extras.music"
              label="Live music"
          />
        </div>
      </fieldset>

      <button class="button -fill-gradient" type="submit">Submit</button>
    </form>
  </div>

  <pre> {{ event }}</pre>

</template>

<script>
import BaseInput from "@/components/BaseInput";
import BaseSelect from "@/components/BaseSelect";
import BaseCheckbox from "@/components/BaseCheckbox";
import BaseRadio from "@/components/BaseRadio";
import BaseRadioGroup from "@/components/BaseRadioGroup";
import axios from "axios"

export default {
  components: {BaseRadioGroup, BaseRadio, BaseCheckbox, BaseSelect, BaseInput},
  data(){
    return {
      categories: [
        'sustainability',
        'nature',
        'animal welfare',
        'housing',
        'education',
        'food',
        'community'
      ],
      event: {
        category: '',
        title: '',
        description: '',
        location: '',
        pets: 1,
        extras: {
          catering: false,
          music: false
        }
      },
      petOptions: [
        {label: 'Yes', value: 1},
        {label: 'No', value: 0},
      ]
    }
  },
  methods: {
    sendForm(){
      axios.post(
          'https://my-json-server.typicode.com/Code-Pop/Vue-3-Forms/events',
          this.event
      ).then(function(response){
        console.log(response)
      }).catch(function(err){
        console.log(err)
      })
    }
  }
}
</script>

<style scoped>
button {cursor:pointer;}
fieldset {margin-bottom:30px; border:none; padding:0;}
legend {font-size:30px; font-weight:700; margin:0 0 10px;}
</style>