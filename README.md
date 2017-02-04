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
```