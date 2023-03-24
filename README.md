Assignment 1
PART 1

Step 1:
After installing docker engine by following the docker docs, i am going to build and run a simple docker image which outputs message. 

Step 2:
viru@viru:~$ sudo docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

Since my local repository is empty i have downloaded the dependencies.

viru@viru:~$ sudo docker pull ubuntu:latest
latest: Pulling from library/ubuntu
2ab09b027e7f: Pull complete
Digest: sha256:67211c14fa74f070d27cc59d69a7fa9aeff8e28ea118ef3babc295a0428a6d21
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

Step3:
Before i create a dockerfile i have created a public repository in github for the README file and dockerfile.
viru@viru:~/Desktop$ mkdir ass1
viru@viru:~/Desktop$ cd ass1
viru@viru:~/Desktop/ass1$ git init
Initialized empty Git repository in /home/viru/Desktop/ass1/.git/
viru@viru:~/Desktop/ass1$ nano README.md
viru@viru:~/Desktop/ass1$ ls
README.md
viru@viru:~/Desktop/ass1$ git add README.md
viru@viru:~/Desktop/ass1$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md

viru@viru:~/Desktop/ass1$ git commit -m "Assignment-1 part-1"
[master (root-commit) 65f43c6] Assignment-1 part-1
 1 file changed, 2 insertions(+)
 create mode 100644 README.md

viru@viru:~/Desktop/ass1$ git push https://github.com/Hamiz823/Ass1p1.git
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream https://github.com/Hamiz823/Ass1p1.git master

viru@viru:~/Desktop/ass1$ git status
On branch master
nothing to commit, working tree clean
viru@viru:~/Desktop/ass1$ git push https://github.com/Hamiz823/Ass1p1.git
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream https://github.com/Hamiz823/Ass1p1.git master

viru@viru:~/Desktop/ass1$ git push --set-upstream https://github.com/Hamiz823/Ass1p1.git master
Username for 'https://github.com': Hamiz823
Password for 'https://Hamiz823@github.com':
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 236 bytes | 59.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/Hamiz823/Ass1p1.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'https://github.com/Hamiz823/Ass1p1.git'.


After that i have created the dockerfile by following commands 
viru@viru:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
viru@viru:~$ cd Desktop
viru@viru:~/Desktop$ cd ass1
viru@viru:~/Desktop/ass1$ touch Dockerfile
viru@viru:~/Desktop/ass1$ ls
Dockerfile  README.md
viru@viru:~/Desktop/ass1$ nano Dockerfile
FROM ubuntu
RUN apt-get update -y
CMD ["echo", "Hello, This is my first image file."]


Step 4:
viru@viru:~/Desktop/ass1$ sudo docker build -t assign1p1:latest .
[+] Building 122.6s (6/6) FINISHED
 => [internal] load build definition from Dockerfile                                                               0.1s
 => => transferring dockerfile: 123B                                                                               0.0s
 => [internal] load .dockerignore                                                                                  0.1s
 => => transferring context: 2B                                                                                    0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                   0.0s
 => [1/2] FROM docker.io/library/ubuntu                                                                            0.0s
 => [2/2] RUN apt-get update -y                                                                                  122.1s
 => exporting to image                                                                                             0.2s
 => => exporting layers                                                                                            0.1s
 => => writing image sha256:76836b45f39f429d6be4d82d24d246005ebe7b6c62af7a711b2ac6a3c8faf30f                       0.0s
 => => naming to docker.io/library/assign1p1:latest                                                                0.0s
viru@viru:~/Desktop/ass1$ sudo docker images
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
assign1p1    latest    76836b45f39f   8 minutes ago   77.8MB
ubuntu       latest    08d22c0ceb15   2 weeks ago     77.8MB

viru@viru:~/Desktop/ass1$ sudo docker run assign1p1
Hello, This is my first image file.

Step 5:
sudo docker tag assign1p1:latest hamiz822/dockerhub:firstimage
viru@viru:~/Desktop/ass1$ sudo docker images
REPOSITORY           TAG          IMAGE ID       CREATED        SIZE
hamiz822/dockerhub   firstimage   76836b45f39f   28 hours ago   77.8MB
assign1p1            latest       76836b45f39f   28 hours ago   77.8MB
ubuntu               latest       08d22c0ceb15   2 weeks ago    77.8MB
viru@viru:~/Desktop/ass1$ sudo docker push hamiz822/dockerhub:firstimage
The push refers to repository [docker.io/hamiz822/dockerhub]
71d24aba432a: Pushed
b93c1bd012ab: Pushed
firstimage: digest: sha256:3cb3d39224e0dcc0ae86b7991ec507848d1dc57a4a0db4776a1f5e025b90517e size: 736

Step 6 and 7:
Done in step 3.

Step 8:
viru@viru:~/Desktop/ass1$ git add Dockerfile
viru@viru:~/Desktop/ass1$ git commit -m "Code"
[master a2943f5] Code
 1 file changed, 3 insertions(+)
 create mode 100644 Dockerfile

viru@viru:~/Desktop/ass1$ git push https://github.com/Hamiz823/Ass1p1.git
Username for 'https://github.com': Hamiz823
Password for 'https://Hamiz823@github.com':
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 358 bytes | 358.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/Hamiz823/Ass1p1.git
   65f43c6..a2943f5  master -> master
Verified that the code is present.
