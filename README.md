
# Gateway API implementation in GKE
`The goal is to replace separate ingress + svc mesh in the long run, to provision and use just 1 load balancer for ALL environments, Live/Dev & canary,(and exposing lots of svcs/APIs) saving huge load balancer costs.`

  - (can be used in aws,azure too)
  - gateway api is a "standard" core feature for k8s - https://gateway-api.sigs.k8s.io/

<br/>

##### gatewayClassName: gke-l7-global-external-managed

`needed gatewayClassName to be able to do cross namespace routing in GKE`
<br/>

##### Namespace live-store

`Production version deploys whenever a merge is made to main/prod branch`
<br/>

##### Namespace dev

`Dev version can be used for everyday "live view" development testing, it deploys whenever a merge is made to dev branch`
<br/>

##### Header based canary deployment `(namespace canary)`

`Header-based canarying lets the service owner match synthetic test traffic that does not come from real users. This is an easy way of validating that the basic features of the application is functioning without exposing users directly`
<br/><br/>
> [!CAUTION]
> (weighted routing is not fully implemented yet as i cannot get the `gke-l7-global-external-managed-mc` gw class to deploy, as it needs a `premiere tier` account type ) but the functionality is already done on our end

<br/>

### Next steps

+ [x] short term: integrating the current working github actions build and deploy

+ [ ] long term: considering using flagger or argo rollouts/argo cd for `drift detection`

      - https://docs.flagger.app/tutorials/gatewayapi-progressive-delivery
      - https://argoproj.github.io/argo-rollouts/features/canary/
  

+ [ ] long term: setting up prometheus+grafana+ loki to completely cover and monitor ALL deployments

<br/>


## Network infrastructure overview



![Logo](https://github.com/misua/progressive-deployment-template/blob/main/base.drawio.png)
<br/>

---

## Authors

- [@misua](https://www.github.com/misua)



`Badges`


[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)

![Static Badge](https://img.shields.io/badge/Charles-Pogi-blue)




