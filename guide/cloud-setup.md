---
description: 'Running sorry-cypress in cloud - AWS, Google Cloud, K8s, Heroku'
---

# Cloud Setup

### Cloud Demo

{% hint style="info" %}
This demo runs on a free Heroku instance, it takes a minute to wake it up when you first navigate 
{% endhint %}

Visit [https://sorry-cypress-demo.herokuapp.com/](https://sorry-cypress-demo.herokuapp.com/) to see the web dashboard in action. 

[Reconfigure your cypress agent](../cypress-agent/cli-one-liners.md) to use `https://sorry-cypress-demo-director.herokuapp.com/`.

```bash
sed -i -e 's|api_url:.*$|api_url: "https://sorry-cypress-demo-director.herokuapp.com/"|g' /*/.cache/Cypress/*/Cypress/resources/app/packages/server/config/app.yml
```

### Cloud Providers

Now you can consider deploying it on your own infrastructure. 

Each service is available as a standalone Docker image at [https://hub.docker.com/u/agoldis](https://hub.docker.com/u/agoldis). The images are automatically updated on each release and tagged in accordance with GitHub release tags.

Sorry-cypress has been successfully used by many organizations of different sizes on different platforms, e.g.:

* Heroku
* AWS
* Google Cloud
* Azure
* Digital Ocean
* IBM Cloud

Check out the rest of the documentation for deployment instructions.

{% hint style="success" %}
Congratulations! You have completed the guide. 

* ⭐️ us on [GitHub](https://github.com/sorry-cypress/sorry-cypress)
* Learn how to [Contribute](../contributions.md)
* If you're stuck, check out [Support](../support.md) options
* Follow [@sorrycypress](https://twitter.com/sorrycypress/) to get the latests updates
{% endhint %}





