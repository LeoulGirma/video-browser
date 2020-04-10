 <template>
  <div>
    <input @keyup.enter="hi" type="text" />
  </div>
</template>
 
 <script>
export default {
  name: "SearchBar",
  data() {
    return {};
  },
  methods: {
    hi(event) {
      this.$emit("termChange", event.target.value);
    }
  }
};
</script>
 
<style scoped>
input {
  width: 60%;
}
div {
  text-align: center;
  margin: 20px;
}
</style>