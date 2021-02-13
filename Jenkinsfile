pipeline
{
    agent any
    stages
	{
	stage('test')
	    {
		steps
		    {
             	withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'deploytos3', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
             	{
					withCredentials([file(credentialsId: 'kp', variable: 'k_p')]) {
						withCredentials([file(credentialsId: 'kp2', variable: 'k_p2')]) {
				sh 'terraform init -no-color'
				sh 'terraform apply -auto-approve -no-color -var "acc=$access" -var "sec=$secr" -var "key_p=$k_p" -var "key_p2=$k_p2"'
			}
    		}
				}
			}
	}
}
}