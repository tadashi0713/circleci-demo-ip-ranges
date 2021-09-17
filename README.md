# Demo for CircleCI IP Ranges features

[![CircleCI](https://circleci.com/gh/tadashi0713/circleci-demo-ip-ranges/tree/master.svg?style=svg&circle-token=d4c42d06de466c88ea5742180505c7ac34142be9)](https://circleci.com/gh/tadashi0713/circleci-demo-ip-ranges/tree/master)

[IP Ranges](https://circleci.com/docs/2.0/ip-ranges/) is a feature for CircleCI customers who need to configure IP-based access to their restricted environments.

This demo shows how to run CircleCI tests([Cypress](https://www.cypress.io/)) to IP-based restricted application using IP Ranges.

<img src="https://user-images.githubusercontent.com/8651308/133713242-a9e4aac0-6200-4b96-8cfe-93ca7ce14c99.png" width="55%">

# IP-based restricted application

* https://circleci-demo-ip-ranges.herokuapp.com (Should return 403: Forbidden)
* Nginx + Static site using React.js
<img src="https://user-images.githubusercontent.com/8651308/133074306-51a45e90-08bc-4be7-90f7-21d8c7df5c9c.png" width="40%">

* [Nginx config](https://github.com/tadashi0713/circleci-demo-ip-ranges/blob/master/nginx.conf)
  * Allow lists of IP address ranges and deny others
  * List of IP address ranges can be found [here](https://circleci.com/docs/2.0/ip-ranges/#listofipaddressranges)

```nginx
server {
  # CircleCI IP Ranges
  allow 107.22.40.20;
  allow 18.215.226.36;
  allow 3.228.208.40;
  ...

  deny all;
```

# Cypress tests with/without IP ranges

```yaml
cypress_with_ip_ranges:
  executor: cypress/browsers-chrome77
  circleci_ip_ranges: true # set true to enable IP Ranges feature
  steps:
    - run:
        name: Show IP address
        command: curl -s https://checkip.amazonaws.com/
    - run: npm run cypress
```

## [cypress_without_ip_ranges](https://app.circleci.com/pipelines/github/tadashi0713/circleci-demo-ip-ranges/45/workflows/c6ef071e-4f00-4cbb-a0ea-7938cc8bd3b6/jobs/146)

<img src="https://user-images.githubusercontent.com/8651308/133714113-86c1a1fc-ab71-400c-907e-1fae8f4320c5.png" width="80%">

## [cypress_with_ip_ranges](https://app.circleci.com/pipelines/github/tadashi0713/circleci-demo-ip-ranges/45/workflows/c6ef071e-4f00-4cbb-a0ea-7938cc8bd3b6/jobs/147)

<img src="https://user-images.githubusercontent.com/8651308/133713980-d6d4c293-afd1-4d86-8ebe-424aa440ed41.png" width="80%">
