pipeline{
	agent{
		label{
			label "built-in"
		}
	}
	stages{
		stage("initial"){
			steps{
				sh "yum install git -y"
				sh "yum install docker -y"
				sh "systemctl start docker"
				sh "rm -rf /mnt/project/*"
				dir("/mnt/project/23Q1")
				{
				    
					sh "git clone https://github.com/aniketc92/deploy1.git -b 23Q1"
					sh "chmod 777 /mnt/*"
				}
				
				dir("/mnt/project/23Q2")
				{
					sh "git clone https://github.com/aniketc92/deploy1.git -b 23Q2"
					sh "chmod 777 /mnt/*"
				}
				dir("/mnt/project/23Q3")
				{
					sh "git clone https://github.com/aniketc92/deploy1.git -b 23Q3"
					sh "chmod 777 /mnt/*"
				}
			}
		}
		stage("parallel stages"){
			parallel{
				stage("stage-1"){
					steps{
					sh "docker run -itdp 80:80 --name 23q1 httpd"
					sh "docker cp /mnt/project/23Q1/deploy-1/index.html 23q1:/usr/local/apache2/htdocs/" 
					}
				}
				stage("stage-2"){
					steps{
					sh "docker run -itdp 90:80 --name 23q2 httpd"
					sh "docker cp /mnt/project/23Q2/deploy-1/index.html 23q2:/usr/local/apache2/htdocs/" 
					}
				}
				stage("stage-3"){
					steps{
					sh "docker run -itdp 81:80 --name 23q3 httpd"
					sh "docker cp /mnt/project/23Q3/deploy-1/index.html 23q3:/usr/local/apache2/htdocs/" 
					}
				}
			}
		}
	}
    
}
