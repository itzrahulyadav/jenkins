# Get started with jenkins

## steps

1. Launch an ec2 instance(ubuntu or amazon linux preferred)
2. connect to the instance 


## install jenkins on aws ec2

- step 1
```
sudo apt update

```
- step 2

```
sudo apt install openjdk-11-jre

```

- step 3

```
java -version

```
The output would look something like this 

```
openjdk version "11.0.12" 2021-07-20 OpenJDK Runtime Environment (build 11.0.12+7-post-Debian-2) OpenJDK 64-Bit Server VM (build 11.0.12+7-post-Debian-2, mixed mode, sharing)

```

- step 4

```
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \   /usr/share/keyrings/jenkins-keyring.asc > /dev/null 



echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \   https://pkg.jenkins.io/debian binary/ | sudo tee \   /etc/apt/sources.list.d/jenkins.list > /dev/null

```

- step 5

```
sudo apt-get update 

sudo apt-get install jenkins

```

- step 6

```
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins

```

Enable port 8080 on security group to run jenkins on port 8080.

3. Login to jenkins

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

```
- The above command will return a string {dhfdhfdkodhdghodgh} paste it into the jenkins administration password.

- Install suggested plugins

- login into jenkins

### Now inside jenkins

1. Create new item

2. Give a name to the project

3. Choose freestyle pipeline

4. Select github project and enter the url

5. Add credentials (we will create ssh keys for connecting)

### inside ec2 write 

```
ssh-keygen

```
6.It will generate public and private key pair(just keep pressing enter)

7.cd .ssh

8. You will find two keys id_rsa and id_rsa.pub

9. id_rsa is private key while id_rsa.pub is public key

```
 cat id_rsa
 
```

10. Copy the hash and open github

### Inside github

1. Open settings

2. go to ssh and gpg keys

3. New ssh key

4. Give it a title

5. Inside the key input paste the hashstring.

6. Add ssh key

7. Open Jenkins and click on credentials.

8. Select ssh username and private key in kind.

9. for username select ubuntu.

10. for private key copy the id_rsa hashstring and paste into the input provided.

11. Id can be anything.

12. for branch select /master

13. click on save.

14. Congo🎉🎉🎉🎉Your github and jenkins is integrated.

