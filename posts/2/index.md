# How to Edit and Upload Code on Local Device to Github

### Preparation tools:  
   .A computer  
   .A github account  
   
// This article uses Linux as an example, and the whole process is in a root environment.

### 安装Git
 Use 
 ``` bash
git --version
```
![](https://i.imgtg.com/2023/07/25/OhVyJa.jpg)
 to see if Git is installed
 ### 配置
 #### 创建密钥
 Create the SSH Key of the project
 ``` bash
 ssh-keygen -t rsa -C &#34;youremail@example.com&#34;
 ```
 ![](https://i.imgtg.com/2023/07/25/OhVgfS.jpg)
 Just press Enter three times and the key will be stored in the default location.  
 Enter the path to view the key
 ``` bash
 cd /root/.ssh
 ```

#### 复制密钥
After the creation is complete, find the .ssh directory in the user&#39;s home directory. There are two files, id_rsa and id_rsa.pub. These two are the secret key pair of SSH Key. id_rsa is the private key and cannot be disclosed. id_rsa.pub is the public key. Key, you can safely tell anyone.  
 Execute 
 
``` bash
vim id_rsa.pub 
```
 ![](https://i.imgtg.com/2023/07/25/OhVpBN.jpg)
to open the public key and copy its content.
![](https://i.imgtg.com/2023/07/25/OhVJKC.jpg)
 #### 添加密钥
Log in to github to register or log in to your account, open the &#34;SSH Keys&#34; page of &#34;settings&#34;, then click &#34;New SSH Key&#34;, fill in any Title, paste the content of the id_rsa.pub file in the Key text box, and click &#34;Add Key&#34;, you should see the added Key
 ![](https://i.imgtg.com/2023/07/25/OhVP0L.png)
 Note that it is SSH, not GPG
 ![](https://i.imgtg.com/2023/07/25/OhVQlU.png)
   
   ![](https://i.imgtg.com/2023/07/25/OhVVMc.jpg)
#### 添加用户信息
Configure username and email

 Configure user name: 
git config --global user.name (user name registered on github)

 Configure user email: 
git config --global user.email (the email address when registering on GitHub)
![](https://i.imgtg.com/2023/07/25/OhVcZv.jpg)
``` bash
git config --global user.name &#34;yourusername&#34;
git config --global user.email &#34;youremail@example.com&#34;
```
Log in to your github account and create a new repository.
![](https://i.imgtg.com/2023/07/25/OhVdcq.jpg)
  
  ![](https://i.imgtg.com/2023/07/25/OhVY7r.jpg)
#### 测试
Go to the repository and copy the HTTPS address of the repository.
![](https://i.imgtg.com/2023/07/25/OhV2JI.jpg)
Git local files to GitHub remote warehouse
Create a TEST folder locally and enter

``` bash
mkdir TEST
```
![](https://i.imgtg.com/2023/07/25/OhVlXG.jpg)
#### 准备上传
Create and edit a file named hello.txt(Please search online for how to use VIM.  And you can use other editors for editing, such as Vscode, Atom.)
![](https://i.imgtg.com/2023/07/25/OhVjz1.jpg)
Back to the terminal command window, initialize the current directory as a version library, add a remote warehouse and synchronize with the local, enter the command as shown below
``` bash
git init
git remote add origin https://github.com/****.git
git pull --rebase origin master
```
![](https://i.imgtg.com/2023/07/25/OhVXTF.jpg)
//Because I didn&#39;t add a readme file when I created it, there are some caveats, so I don&#39;t care about them here.
#### 上传文件
Submit the created hello.txt to the remote warehouse and enter the command as shown below
``` bash
git add hello.txt
git commit -m &#34;first commit&#34;
git push origin master
```
![](https://i.imgtg.com/2023/07/25/OhV6lD.jpg)
Because it is the first time to use, so you need to verify the password and user name.

Now we can log in to github and view it.

---

> 作者: [Haoran Dong](https://github.com/TEWQ-1314)  
> URL: https://www.depth.su/posts/2/  

