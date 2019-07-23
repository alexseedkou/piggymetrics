node("docker") {
    docker.withRegistry('<<your-docker-registry>>', '<<your-docker-registry-credentials-id>>') {
    
        git url: "https://github.com/alexseedkou/piggymetrics.git", credentialsId: 'alexseedkou'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "Docker_build_demo"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}