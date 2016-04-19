# sonarqube-setup
Installation of sonarqube
Installing sonarQube(ubuntu)
Java JRE and a DBMS(postgresql in our case) must be already there
1) create a user called sonar 

createuser –interactive
then role :sonar
give superuser privilages
2)Create Sonar database with the user sonar
CREATE DATABASE sonar
WITH OWNER = sonar
ENCODING = ‘UTF8′
TABLESPACE = pg_default
LC_COLLATE = ‘en_US.UTF-8′
LC_CTYPE = ‘en_US.UTF-8′
CONNECTION LIMIT = -1;
GRANT CONNECT, TEMPORARY ON DATABASE sonar TO public;
GRANT ALL ON DATABASE sonar TO sonar;
 
3)Download and unzip SonarQube distribution
wget http://dist.sonar.codehaus.org/sonarqube-5.1.zip
unzip sonarqube-5.1.zip
or click here then unzip the downloaded file
 
4)Then move sonarqube-5.3 in to /opt/sonar folder
mv sonarqube-5.1 /opt/sonar
5)open opt/sonar/conf/sonar.properties and edit the following lines as follows
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar
sonar.jdbc.url=jdbc:postgresql://localhost/sonar
sonar.web.host=127.0.0.1
sonar.web.context=/sonar
sonar.web.port=9000
6)start the sonarQube
sudo /opt/sonar/bin/linux-x86-64/sonar.sh start
(the you can access sonar qube through the browser using http://localhost:9000/sonar)
Installing sonar Runner
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
or else you can go to /opt/sonar-runner/bin/sonar-runner.bat file and include the above command in it.
6) source ~/.bash_profile
