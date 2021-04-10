---
description: Get started with a free parallelization using sorry-cypress
---

# Get Started

Let's start by running basic sorry-cypress configuration:

```text
docker run -p 1234:1234 agoldis/sorry-cypress-director
```

We've just launched `director` service on [`http://localhost:1234`](http://localhost:1234) - this service coordinates cypress agents and enables free parallelization.

### Re-configuring cypress agent

We need to override cypress agents configuration to start using the local `director` service:

```bash
# Let's find cypress runner location
# Create a script in the package.json of your project: 
# { "debug": "DEBUG=cypress:* cypress version" }

# execute the script using npm or yarn
npm run debug


# Examine the output, note the path
"cypress:cli Reading binary package.json from: /Users/agoldis/Library/Caches/Cypress/7.0.1/Cypress.app/Contents/Resources/app/package.json +0ms"

# Now let's override cypress agent configuration
vim /Users/agoldis/Library/Caches/Cypress/7.0.1/Cypress.app/Contents/Resources/app/packages/server/config/app.yml
production:
  # api_url: "https://api.cypress.io/"
  api_url: "http://localhost:1234/"
```

{% hint style="info" %}
**New!** You can easily set cypress API server URL by using[`cy2`](https://www.npmjs.com/package/cy2) package.  [Read more.](../cypress-agent/cy2.md)
{% endhint %}

### Running cypress tests in parallel <a id="running-cypress-tests-in-parallel"></a>

Let's open several terminal windows and run `cypress` in each. Make sure you have cypress tests defined in advance \(clone [https://github.com/agoldis/sorry-cypress-demo.git](https://github.com/agoldis/sorry-cypress-demo.git) if you don't have any test handy\).

```bash
# run in each terminal
cypress run --parallel --record --key somekey --ci-build-id hello-cypress
```

You'll notice that different instances of cypress agents are running different tests. 

🎉 We've just finished the basic setup of sorry-cypress and ran our tests in parallel!

{% hint style="info" %}
* Use the same `--ci-build-id` to associate different cypress agents with the same run
* You can run as many [cypress agents](../concepts/parallelization-guide.md) as you want - each  will run a different test suite
* This basic `director` configuration keeps all the test results in-memory. Restarting it wipes all the data
{% endhint %}



