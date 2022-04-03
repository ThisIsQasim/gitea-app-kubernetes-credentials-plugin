// buildPlugin()
// Replace with above once finalized
podTemplate(yaml: '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: maven
    image: maven:3.8.4-jdk-11
    command:
    - sleep
    args:
    - infinity
''') {
    node(POD_LABEL) {
        container('maven') {
            checkout scm
            sh 'mvn -B -ntp -Dmaven.test.failure.ignore package'
        }
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts '**/target/*.hpi'
    }
}
