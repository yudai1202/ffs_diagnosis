<template>
  <div class="columns is-centered">
    <div>
      <h1>Result Page</h1>
    </div>
    <div>
      <table class="table">
        <thead>
          <tr>
            <th>A</th>
            <th>B</th>
            <th>C</th>
            <th>D</th>
            <th>E</th>
          </tr>
        </thead>
        <tbody>
            <tr>
              <td>{{ $route.params.factors.a }}</td>
              <td>{{ $route.params.factors.b }}</td>
              <td>{{ $route.params.factors.c }}</td>
              <td>{{ $route.params.factors.d }}</td>
              <td>{{ $route.params.factors.e }}</td>
            </tr>
          </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>

</style>