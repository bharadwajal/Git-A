node {
       maintainer_name = "bj"
       container_name = "apache"
       build_tag = "A"
stage 'clone' 
      git url: 'https://github.com/bharadwajal/Git-A.git'
stage 'Test' 
      sh "mvn clean test" 
stage 'Package' 
      sh "mvn package"
stage 'Build Image'
      echo "Building docker.build(${maintainer_name}/${container_name}:${build_tag})"
      container = docker.build("${maintainer_name}/${container_name}:${build_tag}")
stage 'Running container'
      docker.image("${maintainer_name}/${container_name}:${build_tag}").withRun("--name=${container_name}") { c ->
  echo "Docker Container is running"
      }
}
