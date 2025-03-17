pipeline { 
    agent any
    environment { 
    VENV_DIR = 'venv' 
}
    stages { 
        stage('Checkout') { 
            steps { 
            git branch: 'master', url: 'https://github.com/Beni25-mak/ci-test.git'
    }
}
    stage('Setup') { 
        steps { 
            bat 'python -m venv venv' // Crée un environnement virtuel
            // bat '.\\venv\\Scripts\\pip install -r requirements.txt' // Installe les dépendances
        }
}
    stage('Run Script') { 
        steps { bat '.\\venv\\Scripts\\python app.py' // Exécute le script Python
        } 
}
    stage('Notify') { 
        steps { 
            script { 
                def result = currentBuild.result ?: 'SUCCESS' 
                emailext subject: "Jenkins Build: ${result}", 
                body: "Build Status: ${result}\nVoir Jenkins: ${env.BUILD_URL}", 
                to: 'benimakumbu24@gmail.com' 
                } 
            } 
        } 
}
post { 
    failure { 
        emailext subject: "Echec du build Jenkins",
        body: "Echec du pipeline : ${env.BUILD_URL}", 
        to: 'benimakumbu24@gmail.com' 
        } 
    } 
}

//merci beaucoup pour votre soutiens cela me fait tellement plaisir
//bonne journée
// Je suis très ravie de connaitre tes nouvelles
// je suis une formation sur Machine Learning
// C'est Guillaum le formateur
// Tongo etani beni va dormir
// Je veux dormir je teste seulement les dernières choses.