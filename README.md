# Demo for CircleCI IP Ranges features

[IP Ranges](https://circleci.com/docs/2.0/ip-ranges/) is a feature for CircleCI customers who need to configure IP-based access to their restricted environments.

This demo shows how to run CircleCI tests(Cypress) to IP-based restricted application using IP Ranges.

<img src="https://user-images.githubusercontent.com/8651308/133713242-a9e4aac0-6200-4b96-8cfe-93ca7ce14c99.png" width="55%">

# IP-based restricted application

* https://circleci-demo-ip-ranges.herokuapp.com (Should return 403: Forbidden)
* Nginx + Static site using React.js
* [Nginx config](https://github.com/tadashi0713/circleci-demo-ip-ranges/blob/master/nginx.conf)
  * Allow lists of IP address ranges and deny others
  * List of IP address ranges can be found [here](https://circleci.com/docs/2.0/ip-ranges/#listofipaddressranges)

# Cypress tests with/without IP ranges

## cypress_with_ip_ranges

<img src="https://user-images.githubusercontent.com/8651308/133713980-d6d4c293-afd1-4d86-8ebe-424aa440ed41.png" width="80%">

## cypress_without_ip_ranges

<img src="https://user-images.githubusercontent.com/8651308/133714113-86c1a1fc-ab71-400c-907e-1fae8f4320c5.png" width="80%">
