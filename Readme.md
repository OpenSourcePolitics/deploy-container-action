# Deploy container action

Allows to deploy a Docker container on a Scaleway serverless service.
Uses Scaleway CLI to deploy the container.
Uses Build and push images action to build and push the Docker image.

## inputs:
- registry:
  - description: 'Registry url'
  - required: true
- namespace:
  - description: 'Namespace'
  - required: true
- password:
  - description: 'Password'
  - required: true
- access_key:
  - description: 'Access key'
  - required: true
- username:
  - description: 'Username'
  - required: false
- default: "userdoesnotmatter"
- image_name:
  - description: 'Image name'
  - required: true
- tag:
  - description: 'Image tags'
  - required: true
- container_name:
  - description: 'Container name'
  - required: true
- scw_cli_version:
  - description: 'Scaleway cli version'
  - required: false
- default: "2.14.0"
- project_id:
  - description: 'Scaleway project id'
  - required: true
- organization_id:
  - description: 'Scaleway organization id'
  - required: false
  - default: "00000000-0000-0000-0000-000000000000"

## Usage
```yaml
- name: Deploy container
  uses: OpenSourcePolitics/deploy-container-action@master
  with:
    registry: ${{ vars.REGISTRY_URL }}
    namespace: ${{ vars.REGISTRY_NAMESPACE }}
    password: ${{ secrets.REGISTRY_PASSWORD }}
    access_key: ${{ secrets.SCALEWAY_ACCESS_KEY }}
    image_name: ${{ vars.REGISTRY_IMAGE_NAME }}
    tag: ${{ github.ref }}
    container_name: ${{ vars.CONTAINER_NAME }}
    project_id: ${{ secrets.SCALEWAY_PROJECT_ID }}
```