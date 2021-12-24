DevOps-Project: CI/CD SampleWebApp
---------------------------------

Description / Steps:

Tools: EC2, Git, Github, Java, Jenkins, Tomcat, ANT

1. Install the Git and configure on the machine.
2. Install the Java and configure the environment varible on the machine.
3. Install the Apache Tomcat.
4. Download the Jenkins.war file inside the Tomcat and configure the environment varible for Jenkins.
5. Access the tomcat by using localhost:8080 and for Jenkins use the localhost:8080/jenkins
6. Install the required plugins inside the Jenkins.
7. Install the ANT and configure the environment varible on the machine.
8. Clone the Github repo to local machine.
9. Install the requird plugins in Jenkins.
10. Create a job to pull a code
    manage jenkins --> manage plugins --> github --> install without restart,
    new job --> github pull --> free style project --> ok,
    github pull --> configure --> general --> advance --> use custom workspace --> ${JENKINS_HOME}/workspace/samplewebapp,
    source code management --> git --> < copy github repo URL & paste >,
11. Build & review code and publish result
    manage jenkins --> manage plugins --> ANT & warning next gen plugin --> install without restart,
    new item --> build and code review --> free style project --> ok,
    general --> advance --> use custom workspace --> ${JENKINS_HOME}/workspace/samplewebapp,
    source code management --> git --> < copy github repo URL & paste >,
    build --> invoke ANT,
    post build action --> publish result analysis --> checkstyle_errors.xml --> save,
12. Run tests and publish JUnit tests report
    manage jenkins --> manage plugins --> JUnit realtime test reportes plugin --> install without restart,
    new item --> Unit Test --> free style project --> ok,
    general --> advance --> use custom workspace --> ${JENKINS_HOME}/workspace/samplewebapp,
    source code management --> git --> < copy github repo URL & paste >,
    build --> invoke ANT,
    post build action --> publish JUnit test result --> test calculator --> save,
13. Deploy code to production
    manage jenkins --> manage plugins --> deploy to container --> install without restart,
    new item --> deploy --> free style project --> ok,
    general --> advance --> use custom workspace --> ${JENKINS_HOME}/workspace/samplewebapp,
    source code management --> git --> < copy github repo URL & paste >,
    build --> invoke ANT, Target --> war,
    post build action --> deploy war/ear to container add container --> Tomcat 9.0,
    URL --> https://localhost:8080 --> save,
14. CI/CD build pipeline
    manage jenkins --> manage plugins --> build pipeline --> install without restart,
    github pull --> configure --> post build action --> build other project --> build and code review --> save,
    build and code review --> configure --> post build action --> build other project --> unittest --> save,
    unittest --> configure --> post build action --> build other project --> deploy --> save,
15. Click on (+) --> complete pipeline --> build pipeline view --> ok --> select initial job --> github pull --> ok
    github pull --> configure --> poll scm --> *****,

