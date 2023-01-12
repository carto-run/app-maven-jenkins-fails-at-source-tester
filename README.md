# app-maven-jenkins-fails-at-source-tester

## Creating the Workload

```
tanzu apps workload create app-maven-jenkins-fails-at-source-tester \
  --namespace dev \
  --git-branch main \
  --git-repo https://github.com/carto-run/app-maven-jenkins-fails-at-source-tester \
  --label apps.tanzu.vmware.com/has-tests=true \
  --label app.kubernetes.io/part-of=app-maven-jenkins-fails-at-source-tester \
  --type web \
  --param-yaml testing_pipeline_matching_labels='{"apps.tanzu.vmware.com/pipeline":"jenkins-pipeline"}' \
  --param-yaml testing_pipeline_params='{"secret-name":"jenkins-credentials","job-name":"demo-build","job-params":"[{\"name\":\"GIT_URL\",\"value\":\"https://github.com/carto-run/app-maven-jenkins-fails-at-source-tester\"}]"}' \
  --yes
```

## Logs

```
tanzu apps workload tail app-maven-jenkins-fails-at-source-tester
```

## Configuration

| Item            | Config                                                                                                |
| --------------- | ----------------------------------------------------------------------------------------------------- |
| Scan Policy     | [default](resources/scan-policy.yaml)                                                                 |
| Pipeline        | [developer-defined-jenkins-tekton-pipeline](resources/developer-defined-jenkins-tekton-pipeline.yaml) |
| tap-values.yaml | na                                                                                                    |
| Supply Chain    | source-test-scan-to-url                                                                               |

