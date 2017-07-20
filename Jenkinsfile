node {

maintainer_name = "bj"
container_name = "apache"
build_tag = A
stage 'Clone' 
git url: 'https://github.com/bharadwajal/Git-A.git'

stage 'Test' 
        rtMaven.run pom: 'pom.xml', goals: 'clean test'

stage 'Package' 
        rtMaven.run pom: 'pom.xml', goals: 'package', buildInfo: buildInfo

stage 'Build Image'
	echo "Building docker.build(${maintainer_name}/${container_name}:${build_tag})"
	container = docker.build("${maintainer_name}/${container_name}:${build_tag}")

stage 'Running container'
	docker.image("${maintainer_name}/${container_name}:${build_tag}").withRun("--name=${container_name}")
}
