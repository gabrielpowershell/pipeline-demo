echo 'Hello World'

stage "build"

node {
      git 'https://github.com/jenkinsci/docker'
      bat """
          dir
      """
}

stage "test"

node {
  git 'https://github.com/jenkinsci/docker'
  echo "foo is $foo"
  if (foo == 'true') {
    echo "foo is true"
    bat 'dir'
  } else {
    echo "foo is false"
    bat 'type docker-compose.yml'
  }
  
  for (def i = 0; i < 2; i++) {
  echo "building… $i"
  sleep 1
}
}

stage "package"
echo "step 5"
echo "step 6"

checkpoint 'packaged'

stage name: "acceptance-test"

node {
    for (def i = 0; i < 4; i++) {
        echo "building main... $i"
        sleep 1
    }
}

checkpoint 'accepted'

stage "deploy"

input message: 'Is it ok to push to server ?', ok: '\'Yes, please do\''

echo "Deploying to server."
