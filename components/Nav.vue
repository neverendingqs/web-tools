<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
    <nuxt-link class="navbar-brand" to="/">Tools</nuxt-link>
    <ul class="navbar-nav d-flex justify-content-end">
      <li>
        <a
          class="nav-link"
          href="https://oauth2-client-shell.neverendingqs.com/"
        >
          OAuth 2.0 Client Shell
        </a>
      </li>
      <li>
        <a class="nav-link" href="https://pprint-ndjson.neverendingqs.com/">
          Pretty-Print Newline-Delimited JSON
        </a>
      </li>
      <li>
        <a class="nav-link" href="https://string-utils.neverendingqs.com/">
          String Utils
        </a>
      </li>
      <li>
        <nuxt-link class="nav-link" to="/wsg">Waste Some Guids</nuxt-link>
      </li>
    </ul>
  </nav>
</template>
