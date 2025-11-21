pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/cbbegermanandrerosasfi-ux/Demo-Serenity-Cucumber1.git'
      }
    }
    stage('Build & Test') {
      steps {
        bat 'mvn clean verify'
      }
    }
    stage('Report') {
      steps {
        publishHTML(
            // Usa un array para pasar la configuración del reporte
            target: [
                allowMissing: false,          // El reporte es obligatorio, si falta, falla el build
                alwaysLinkToLastBuild: true,  // Enlaza siempre a la última compilación
                keepAll: true,                // Conserva los reportes de todas las builds
                reportDir: 'target/site/serenity',
                reportFiles: 'index.html',
                reportName: 'Serenity Report'
            ]
        )
      }
    }
  }
}
