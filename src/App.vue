<template>
  <div class="container">
    <ArticleListPage
      :articles="articles"
      @sort-by-votes="sortByVotes"
      @sort-by-dates="sortByDates"
    />
  </div>
</template>

<script>
import ArticleListPage from "./components/ArticleListPage.vue";
import dayjs from "dayjs";

export default {
  name: "App",
  components: {
    ArticleListPage
  },
  data() {
    return {
      articles: []
    };
  },
  methods: {
    sortByVotes(order) {
      if (order === "asc") {
        this.articles = this.articles.sort((a, b) => {
          return a.upvotes - b.upvotes;
        });
      } else if (order === "desc") {
        this.articles = this.articles.sort((a, b) => {
          return b.upvotes - a.upvotes;
        });
      } else {
        return this.articles;
      }
    },
    sortByDates() {
      this.articles = this.articles.sort((a, b) => {
        return (
          dayjs(b.date.valueOf(), "YYYY-MM-DD") -
          dayjs(a.date.valueOf(), "YYYY-MM-DD")
        );
      });
    }
  },
  created() {
    this.articles = [
      {
        title:
          "2 million malicious emails bypassed secure email defenses over 12 months",
        upvotes: 12,
        date: "2020-01-12"
      },
      {
        title:
          "UPDATE 1-Facebook wraps up deals with Australian media firms, TV broadcaster SBS excluded",
        upvotes: 6,
        date: "2021-06-03"
      },
      {
        title:
          "Exclusive-Polish gene project moves to drop Chinese tech on data concerns",
        upvotes: 89,
        date: "2018-09-01"
      },
      {
        title: "The Mercenary Threat of U.S. Hackers-for-Hire",
        upvotes: 43,
        date: "2019-04-09"
      },
      {
        title:
          "Mexico's Kavak drives away with $700M in new funding, doubling its valuation to $8.7B",
        upvotes: 10,
        date: "2012-07-10"
      },
      {
        title: "Bitcoin Price Shockingly Plunges To $5,402 After Pyth Error",
        upvotes: 3,
        date: "2011-01-11"
      },
      {
        title:
          "LabGenius Appoints Dr. Didier Landais as Chief Operating Officer",
        upvotes: 23,
        date: "2021-02-09"
      },
      {
        title: "ADNOC boosts size of drilling unit IPO to $1.1 billion",
        upvotes: 34,
        date: "2016-05-06"
      }
    ];
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 1000px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 6px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
