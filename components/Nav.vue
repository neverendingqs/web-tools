<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
    <ul class="navbar-nav d-flex justify-content-end">
      <a
        class="navbar-brand"
        href="https://neverendingqs.com/"
        target="_blank"
        rel="noopener noreferrer"
      >
        neverendingqs
      </a>
      <li>
        <nuxt-link class="nav-link" to="/">Home</nuxt-link>
      </li>
      <li>
        <external-link
          classes="nav-link"
          href="https://oauth2-client-shell.neverendingqs.com/"
        >
          OAuth 2.0 Client Shell
        </external-link>
      </li>
      <li>
        <external-link
          classes="nav-link"
          href="https://pprint-ndjson.neverendingqs.com/"
        >
          Pretty-Print Newline-Delimited JSON
        </external-link>
      </li>
      <li>
        <nuxt-link class="nav-link" to="/stringutils">String Utils</nuxt-link>
      </li>
      <li>
        <nuxt-link class="nav-link" to="/wsg">Waste Some Guids</nuxt-link>
      </li>
    </ul>
    <ul class="navbar-nav d-flex justify-content-end ml-auto">
      <li>
        <external-link
          classes="nav-link"
          href="https://github.com/neverendingqs/web-tools"
        >
          Source Code
        </external-link>
      </li>
    </ul>
  </nav>
</template>

<script>
import ExternalLink from '~/components/ExternalLink';

export default {
  components: {
    ExternalLink,
  },
};
</script>
