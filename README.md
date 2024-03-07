
# Gateway API in GKE

Purpose of this is to use gw api, to replace ingress + svc mesh, to provision and use 1 load balancer for all environments, Live,dev and canary, saving load balancer costs

#### gatewayClassName: gke-l7-global-external-managed

`needed gatewayClassName to be able to do cross namespace routing in GKE`


#### Namespace live-store

`Production version deploys whenever a merge is made to main/prod branch`


#### Namespace dev

`Dev version is used for everyday development, it deploys whenever a merge is made to dev branch`


#### Header based canary deployment `(namespace canary)`

`Header-based canarying lets the service owner match synthetic test traffic that does not come from real users. This is an easy way of validating that the basic features of the application is functioning without exposing users directly`

` (this is not fully implemented yet as i cannot get the gke-l7-global-external-managed-mc to deploy, as it needs a premier tier account type ) but the functionality is already done` 


### TODO
+ short term: integrating the current working github actions build and deploy

+ considering using flagger or argo rollouts/argo cd for `drift detection`
  - https://docs.flagger.app/tutorials/gatewayapi-progressive-delivery
  - https://argoproj.github.io/argo-rollouts/features/canary/
  

+ setting up prometheus+grafana+ loki to completely cover and monitor ALL deployments


---

## Authors

- [@misua](https://www.github.com/misua)



`Badges`


[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)

![Static Badge](https://img.shields.io/badge/Charles-Pogi-blue)

## Network infrastructure overview



![Logo](https://github.com/misua/progressive-deployment-template/blob/main/base.drawio.png)



