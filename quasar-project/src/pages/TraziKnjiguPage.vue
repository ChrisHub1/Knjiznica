<template>
  <q-page>
    <div class="q-pa-md">
      <q-card flat bordered>
        <q-card-section>
          <div class="text-h4 text-primary text-center q-mb-md">Pretraživanje</div>
          <p class="text-body1 text-center">
            Pretražite bazu knjiga po naslovu ili autoru.
          </p>
        </q-card-section>

        <q-card-section>
          <!-- Pretraga inputa -->
          <q-input
            v-model="searchQuery"
            label="Unesite pojam za pretraživanje"
            :debounce="300"
          />
          <q-checkbox v-model="searchByAuthor" label="Pretraži po autoru" />
          <q-checkbox v-model="searchByTitle" label="Pretraži po naslovu" />
          <q-btn color="primary" label="Traži" @click="searchBooks" />
        </q-card-section>

        <q-card-section>
          <q-table
            :rows="foundBooks"
            :columns="columns"
            row-key="title"
            bordered
            flat
          />
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const searchQuery = ref("");
    const searchByAuthor = ref(false);
    const searchByTitle = ref(false);
    const foundBooks = ref([]);

    const books = [
      {
        title: "The Great Gatsby",
        author: "F. Scott Fitzgerald",
        genre: "Classic",
        year: 1925,
        pages: 180,
        samples: 5,
      },
      {
        title: "1984",
        author: "George Orwell",
        genre: "Dystopian",
        year: 1949,
        pages: 328,
        samples: 3,
      },
      {
        title: "To Kill a Mockingbird",
        author: "Harper Lee",
        genre: "Drama",
        year: 1960,
        pages: 281,
        samples: 7,
      },
      {
        title: "Moby-Dick",
        author: "Herman Melville",
        genre: "Adventure",
        year: 1851,
        pages: 635,
        samples: 2,
      },
      {
        title: "Pride and Prejudice",
        author: "Jane Austen",
        genre: "Romance",
        year: 1813,
        pages: 279,
        samples: 4,
      },
    ];

    const columns = [
      { name: "title", label: "Title", align: "left", field: "title" },
      { name: "author", label: "Author", align: "left", field: "author" },
      { name: "genre", label: "Genre", align: "left", field: "genre" },
      { name: "year", label: "Year", align: "left", field: "year" },
      { name: "pages", label: "Pages", align: "left", field: "pages" },
      { name: "samples", label: "Samples", align: "left", field: "samples" },
    ];

    function searchBooks() {
      foundBooks.value = books.filter((book) =>
        (searchByAuthor.value && book.author.toLowerCase().includes(searchQuery.value.toLowerCase())) ||
        (searchByTitle.value && book.title.toLowerCase().includes(searchQuery.value.toLowerCase()))
      );
    }

    foundBooks.value = books;

    return { searchQuery, searchByAuthor, searchByTitle, foundBooks, columns, searchBooks };
  },
};
</script>

<style scoped>
.q-card {
  margin-top: 20px;
  background-color: #fff;
}

.q-page {
  background-color: #f4f4f4;
  color: #333;
}
</style>
