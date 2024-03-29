# nuxt-spa-terraform-template

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out the [documentation](https://nuxtjs.org).

## Deploy

```bash
$ yarn install
$ yarn run build
# s3 に dist/ を同期
$ aws s3 sync dist/ s3://${DEPLOY_BUCKET} --delete
# cloudfrontのキャッシュ全て（--paths "/*"） を削除
$ aws cloudfront create-invalidation --distribution-id ${DISTRIBUTION_ID} --paths "/*" --region ap-northeast-1
```

## Building

```
terraform init
terraform plan -var-file=terraform.dev.tfvars
terraform apply -var-file=terraform.dev.tfvars
terraform destroy -var-file=terraform.dev.tfvars
```
