<template>
  <div>
    <Navbar />
    <div>
      <div class="nav-background"></div>
      <div class="header">
        <div class="wrapper">
          <div class="row">
            <div class="col lg-12">
              <h1 class="header-title">Blog</h1>
              <div class="header-description">
                News, stories and tips on project management, collaboration
                &amp; productivity
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="section">
        <div class="wrapper">
          <div class="row-2">
            <div
              class="col-2 lg-4 sm-2"
              v-for="article in articles"
              :key="article.id"
            >
              <router-link
                :to="'/blog/' + article.title"
                class="blog-thumbnail-container no-border w-inline-block"
                ><img :src="article.urlToImage" width="533" alt="" />
                <div class="padding no-horizontal-padding">
                  <div class="flex-horizontal">
                    <p class="paragraph-small meta-info">
                      {{ article.publishedAt }}
                    </p>
                    <p class="paragraph-small-2 divider-line">|</p>
                    <p class="paragraph-small meta-info">
                      {{ article.author }}
                    </p>
                  </div>
                  <h3 class="blog-grid-title">{{ article.title }}</h3>
                  <p class="paragraph-small">{{ article.content }}</p>
                </div></router-link
              >
            </div>

            <div class="col-2">
              <div class="paging-container">
            <div><span class="paging-arrow">&lt;</span> <span class="paging-number current">1</span> <span class="paging-number">2</span> <span class="paging-number">3</span> <span class="paging-number">4</span> <span class="paging-number">5</span> <span class="paging-arrow">&gt;</span></div>
          </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "Blog",
  components: {
    Navbar,
  },
  data() {
    return {
      articles: [],
      totalRows: Number,
    };
  },
  methods: {
    setData(data) {
      this.articles = data.articles;
      this.totalRows = data.totalResults;
    },
  },

  mounted() {
    axios
      .get(
        "https://newsapi.org/v2/top-headlines?country=id&apiKey=87e1efe464e74e21b22c58129ba7bbe7"
      )
      .then((response) => this.setData(response.data)) // handle success
      .catch((error) => console.log("Gagal :", error)); // handle error
  },
};
</script>