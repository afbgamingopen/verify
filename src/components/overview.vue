<script setup>
</script>

<template>
  <div class="content">
      <div>
          <h2>Solving the Trust Issue with Online Gambling</h2>
          <p>The underlying concept of <a href="https://en.wikipedia.org/wiki/Provably_fair" rel="external noreferrer noopener"
                  target="_blank">provable fairness</a>
              is that players have the ability to prove
              and verify that their results are fair and unmanipulated. This is achieved through the use of a 
              <a href="https://en.wikipedia.org/wiki/Commitment_scheme" rel="external noreferrer noopener" target="_blank"
                  weight="semibold">commitment scheme<i class="el-icon-link"></i></a>
              , along with cryptographic hashing.</p>
          <p>The commitment scheme is used to ensure that the player has an influence on all results generated.
              Cryptographic hashing is used to ensure
              that the casino also remains honest to
              this commitment scheme. Both concepts combined creates a trust-less environment when gambling online.</p>
          <p>This is simplified in the following representation:</p>
          <p>
          <pre>
              <code>fair result = operators input (hashed) + customers input</code>
          </pre>
          </p>
          <h2>3rd Party Verification</h2>
          <p>All bets are verifiable
            Here and through 3rd party sites that are also open source validators. you can
            Found them by googling, the list is some third party sites:
          </p>
            <ul class="list">
                <li>
                    <a href="https://www.devglan.com/online-tools/hmac-sha256-online" target="_blank"> 
                        <span>
                            https://www.devglan.com/online-tools/hmac-sha256-online 
                        </span>
                    </a>
                </li>
                <li>
                    <a href="https://www.freeformatter.com/hmac-generator.html" target="_blank"> 
                        <span>
                            https://www.freeformatter.com/hmac-generator.html
                        </span>
                    </a>
                </li>
                <li>
                    <a href="https://codebeautify.org/hmac-generator" target="_blank"> 
                        <span>
                            https://codebeautify.org/hmac-generator
                        </span>
                    </a>
                </li>
            </ul>
      </div>
  </div>
</template>

<style scoped>
ul.list {
  padding: 1.5em;
}
</style>
