<template>
  <div class="q-pa-md">
    <q-table
      title="Books"
      :rows="rows"
      :columns="columns"
      row-key="title"
    />
  </div>
</template>

<script>
const columns = [
  {
    name: 'title',
    required: true,
    label: 'Book Title',
    align: 'left',
    field: row => row.title,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'author', align: 'center', label: 'Author', field: 'author', sortable: true },
  { name: 'genre', label: 'Genre', field: 'genre' },
  { name: 'year', label: 'Year', field: 'year', sortable: true },
  { name: 'pages', label: 'Pages', field: 'pages' },
  { name: 'samples', label: 'Stored Samples', field: 'samples', sortable: true, align: 'center' }
]

const rows = [
  {
    title: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    genre: 'Classic',
    year: 1925,
    pages: 180,
    samples: 5
  },
  {
    title: '1984',
    author: 'George Orwell',
    genre: 'Dystopian',
    year: 1949,
    pages: 328,
    samples: 3
  },
  {
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    genre: 'Drama',
    year: 1960,
    pages: 281,
    samples: 7
  },
  {
    title: 'Moby-Dick',
    author: 'Herman Melville',
    genre: 'Adventure',
    year: 1851,
    pages: 635,
    samples: 2
  },
  {
    title: 'Pride and Prejudice',
    author: 'Jane Austen',
    genre: 'Romance',
    year: 1813,
    pages: 279,
    samples: 4
  }
]

export default {
  setup () {
    return {
      columns,
      rows
    }
  }
}
</script>
