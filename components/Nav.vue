<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
    <nuxt-link class="navbar-brand" to="/">Tools</nuxt-link>
    <ul class="navbar-nav d-flex justify-content-end ml-auto">
      <li>
        <nuxt-link class="nav-link" to="/o2cs">
          OAuth 2.0 Client Shell
        </nuxt-link>
      </li>
      <li>
        <a class="nav-link" href="https://pprint-ndjson.neverendingqs.com/">
          Pretty-Print Newline-Delimited JSON
        </a>
      </li>
      <li>
        <nuxt-link class="nav-link" to="/stringutils">
          String Utils
        </nuxt-link>
      </li>
      <li>
        <nuxt-link class="nav-link" to="/wsg">Waste Some Guids</nuxt-link>
      </li>
    </ul>
  </nav>
</template>
