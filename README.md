# Yassir Platform Engineering Take Home Challenge

## 1. Prerequisite.

Install The latest version of the following:
- Docker and Docker-Compose : https://docs.docker.com/engine/install/ 
- Python : https://www.python.org/downloads/ 
- Terraform : https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli
- Git : https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
- Node : https://nodejs.org/en/download/package-manager
- PNPM : https://pnpm.io/installation
- Typescript : https://www.typescriptlang.org/download
- CDKTF : https://developer.hashicorp.com/terraform/tutorials/cdktf/cdktf-install
- TSX : npm i -g tsx

## 2. Deploy Hashicorp/hashicups.

There are 2 Ways to Install Hashicups Provider.
- Install Hashicups as Local Provider : https://developer.hashicorp.com/terraform/plugin/sdkv2#install-hashicups-provider
- Use a Ready Provider created by Some Devs (i will use this option) : https://registry.terraform.io/providers/ahmedhesham6/hashicups/0.3.2
`Note : The offical Hashicups provider Deprecated.`
Check the following Path : packages/iac/cdktf.json

## 3. Installation Steps:

- Install Dependencies : `pnpm install`
- Run Hashicups (Containers) : `cd packages/iac/hashicups-provider && docker-compose up -d`
- Create a Hashicups User : `curl -X POST localhost:19090/signup -d '{"username":"education", "password":"test123"}'`

## 4. Create Dummy Orders/Items.

* order specific folder under `~/cdk_hashicups/packages/iac/resources/`
* items for each order(s) as JSON file under order specific folder(s). 

## 5. Deploy the Stack.

```
cd cdk_hashicups/packages/iac
cdktf get
cdktf plan
cdktf deploy
```

`you can see the orders (order1 and order2 etc.) and the items inside this file ~/cdk_hashicups/packages/iac/cdktf.out/stacks/stack/cdk.tf.json`

## 6. Add/Update/Remove Orders/Items.

To Add a new order/items, we should go through the following steps: 
- Create file `packages/iac/resources/order[x]/item[x]`. 
- Add file content from any exiting items and then change the quantity number and id.
- Update `~/cdk_hashicups/packages/iac/main.ts` to add/remove the new order in this line `MyStack(app, "stack", { resourcePath: ["order1","order2", "order[0-100]"]});`
- Run cdktf plan/deploy for adding items.

