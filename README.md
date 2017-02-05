# Serverless Ansible Build Plugin

serverless.yml
```
plugins:
  - serverless-ansible-build-plugin
```

By default region is replaced with `{{ region }}`, stage with `{{ stage }}` and artifact path `{{ artifact_path }}`. Build directory, where the j2 template and zip is created is `.ansible`.

To change to custom values, those can be defined in `custom` block.
 
```
custom:
  ansible:
    buildDirectory: ".ansible"
    region: "{{ region }}"
    stage: "{{ stage }}"
    artifactPath: "{{ artifact_path }}"
    environment:
      SECRET: "{{ secret }}"

```

To overwrite Lambda environmental variables defined in Serverless service provider, one option is to define those in custom ansible environment and use in provider environment:

```
provider:
  name: aws
  runtime: nodejs4.3
  environment:
    SECRET: ${env:SECRET, self:custom.ansible.environment.SECRET}
```