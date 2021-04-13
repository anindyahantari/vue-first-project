<template>
  <div>
    <Navbar />

    <div class="section">
      <div class="wrapper">
        <div class="row">
          <div class="col-2 lg-6 md-4">
            <h1 class="no-margin">
              {{ article.title }}
            </h1>
          </div>
        </div>
      </div>
    </div>
    <div class="section">
      <div class="wrapper">
        <div class="row-2 centre-align">
          <div class="col-2 lg-6 md-3 sm-2">
            <div class="rich-text-block w-richtext">
              <figure
                style="max-width: 640pxpx"
                id="w-node-c07329d562ea-9667c6c1"
                class="w-richtext-align-fullwidth w-richtext-figure-type-image"
              >
                <div>
                  <img
                    :src="article.urlToImage"
                    width="255"
                    alt=""
                  />
                </div>
              </figure>                
              <p>{{article.content}}</p>
              
            </div>
          </div>
        </div>
      </div>
      <div class="wrapper margin-top">
        <h2 class="wrapper-3 related-title">Related content</h2>
        <div class="row-2 no-bottom-margins">
          <div class="col-2 lg-6">
            <div class="big-blog-thumbnail-container">
              <a href="#" class="works-link w-inline-block"
                ><img
                  src="assets/images/Screen-Shot-2019-05-24-at-14.20.59.JPG"
                  width="616"
                  srcset="
                    assets/images/Screen-Shot-2019-05-24-at-14.20.59-p-500.jpeg 500w,
                    assets/images/Screen-Shot-2019-05-24-at-14.20.59.JPG        631w
                  "
                  sizes="(max-width: 479px) 87vw, (max-width: 767px) 90vw, 45vw"
                  alt=""
                  class="column-image"
                />
                <div class="centre-align">
                  <h4 class="no-bottom-margins-2 related-post-title">
                    Is Our Desire For Safety Causing Us Harm?
                  </h4>
                  <p class="low-opacity-2">Self improvement</p>
                </div></a
              >
            </div>
          </div>
          <div class="col-2 lg-6">
            <div class="big-blog-thumbnail-container">
              <a href="#" class="works-link w-inline-block"
                ><img
                  src="assets/images/sruvs.jpeg"
                  width="616"
                  alt=""
                  class="column-image"
                />
                <div class="centre-align">
                  <h4 class="no-bottom-margins-2 related-post-title">
                    Defining a Modular Type Scale for Web UI
                  </h4>
                  <p class="low-opacity-2">User Interface</p>
                </div></a
              >
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
  name: "SingleBlog",
  components: {
    Navbar,
  },
//   article: this.getArticle(),
  data() {
    return {
      article: [],
    };
  },
  methods: {
    setArticles(articles) {
        articles.forEach(item => {
            if(item.title === this.$route.params.slug)
            {
                this.article = item;
            }
            
        });  
    },
  },

  mounted() {
    axios
      .get(
        "https://newsapi.org/v2/top-headlines?country=id&apiKey=87e1efe464e74e21b22c58129ba7bbe7"
      )
      .then((response) => this.setArticles(response.data.articles)) // handle success
      .catch((error) => console.log("Gagal :", error)); // handle error
  },
};
</script>

<style>
</style>