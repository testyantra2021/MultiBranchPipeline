node('master'){

	stage('SCM Checkout'){
		git url:"https://github.com/testyantra2021/MultiBranchPipeline.git",branch:"master"
	}
	
    stage('Compile-Compile'){
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn compile"
    }

    stage('Compile-Package'){
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
    }
	
    stage('Generate-TestFile'){
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn test"
      
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

