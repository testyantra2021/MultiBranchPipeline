node('master'){

	stage('SCM Checkout'){
		git url:"https://github.com/testyantra2021/SimpleCustomerApp.git",branch:"master"
	}
	
	
	stage('clean the workspace'){
		sh "/usr/share/apache-maven/bin/mvn clean"
			
	}
	
	stage('Compile the code'){
		sh "/usr/share/apache-maven/bin/mvn compile"
	}
		
	stage('Packaging the code'){
		sh "/usr/share/apache-maven/bin/mvn package"
	}	
	
	stage('Junit Testing Reports'){
		junit '**/target/surefire-reports/*.xml'
	}

	stage('jacoco reports'){
          jacoco(
                execPattern: '**/target/jacoco.exec',
                classPattern: '**/coverage/**',
                sourcePattern: '**/coverage/**',
                inclusionPattern: '**/*.class'
		)
   	}
	
}
