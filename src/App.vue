<template>
  <div class="wrapper">
    <!-- <Header :title="title" :links="links" /> -->
    <Header />
    <div class="wrapper-content">
      <div class="container">
        <router-view />
      </div>
    </div>
    <!-- <Footer :links="links" /> -->
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/Header";
// import TheHeader from "@/components/Header";
import Footer from "@/components/Footer";
// import TheFooter from "@/components/Footer";

export default {
  components: {
    Header,
    // Header: TheHeader,
    Footer,
    // Footer: TheFooter,
  },
  // data() {
  //   return {
  //     title: "Template",
  //     links: [
  //       {
  //         title: "Home",
  //         alias: "home",
  //         url: "/",
  //       },
  //       {
  //         title: "About",
  //         alias: "about",
  //         url: "/about",
  //       },
  //       {
  //         title: "Vacancy",
  //         alias: "vacancy",
  //         url: "/vacancy",
  //       },
  //     ],
  //   };
  // },
};
</script>

<style lang="scss">
</style>