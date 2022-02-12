# Demo project for https://github.com/spring-projects/spring-boot/issues/29756

To reproduce the issue, execute the following steps in order:

1. `mvn clean package` <br />
**Outcome**: the image is built correctly, but not pushed. <br />
Also, the following logs are shown:
    > [WARNING] The property 'docker.credentials.username' is not set or it's blank, therefore no image will be pushed.<br/>
    [WARNING] The property 'docker.credentials.password' is not set or it's blank, therefore no image will be pushed.

2. `mvn clean package -Ddocker.credentials.username=something` <br />
**Outcome**: the following logs are shown 

    > [WARNING] The property 'docker.credentials.password' is not set or it's blank, therefore no image will be pushed.
   
     and the build failing with
    
    > [ERROR] Failed to execute goal org.springframework.boot:spring-boot-maven-plugin:2.6.3:build-image (build-image) on project demo: Execution build-image of goal org.springframework.boot:spring-boot-maven-plugin:2.6.3:build-image failed: Invalid Docker publish registry configuration, either token or username/password must be provided
