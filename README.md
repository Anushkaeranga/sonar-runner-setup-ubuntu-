sonarQube should be already installed

1)Download and unzip SonarQube Runner distribution

wget http://repo1.maven.org/maven2/org/codehaus/sonar/runner/sonar-runner-dist/2.4/sonar-runner-dist-2.4.zip
unzip sonar-runner-dist-2.4.zip
or click here then unzip the file

2)move sonar-runner-dist-2.4.zip into /opt/sonar-runner
mv sonar-runner-2.4 /opt/sonar-runner

3) go to /opt/sonar-runner/conf/sonar-runner.properties and uncomment the following lines
sonar.host.url=http://localhost:9000/sonar
sonar.jdbc.url=jdbc:postgresql://localhost/sonar
sonar.sourceEncoding=UTF-8
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar

4) then in the terminal execute: nano ~/.bash_profile
5) then,
export SONAR_RUNNER_HOME=/opt/sonar-runner
PATH=”/opt/sonar-runner/bin:${PATH}”
export PATH
