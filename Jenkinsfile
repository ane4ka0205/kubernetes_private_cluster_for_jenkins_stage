pipeline{
    agent any
    parameters {
      string(defaultValue: "plan",  name: "action",  description: "Do you want plan/apply/destroy ")
    }
        stages{
            stage("Pull repo"){
                steps{
                    git 'https://github.com/ane4ka0205/terraform.git'
                }
            }
            stage("Terraform init"){
                steps{
                    ws("${workspace}/stage/kubernetes_cluster_private"){
                        sh "terraform init"
                    }
                }
            }
            stage("Terraform apply"){
                steps{
                    ws("${workspace}/stage/kubernetes_cluster_private"){
                        sh "terraform ${action} -auto-approve"
                }
            }
        }
    }
}
