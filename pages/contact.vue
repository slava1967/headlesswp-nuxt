<template>
  <div>
    <Contact />
  </div>
</template>

<script>
  import Contact from "~/components/Contact";
  export default {
    components: {
      Contact
    },
    head(){
      return {
        title: "Meipaly | Contact"
      }
    }
  }
</script>