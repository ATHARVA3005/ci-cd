# AIM: Deploy a CICD Pipeline using GitHub Actions for a Nodejs application.
## Workflow
-> Create a GitHub Repository named CICD:

![image](https://user-images.githubusercontent.com/96117491/236533261-f18d4cb4-6fcc-4ebc-afec-9ea7b324ac56.png)

-> Push the local machine code files into the GitHub Repository:

![image](https://user-images.githubusercontent.com/96117491/236533653-87fdb913-ce03-487a-a90c-7e9c22a96061.png)

-> Create an ec2 Instance:

![image](https://user-images.githubusercontent.com/96117491/236533818-6e04fd73-f8bc-4d21-9ba4-9aac6d5f12b9.png)

-> Our Nodejs application runs on Port 8000 so we need to update the inbound rules:

![image](https://user-images.githubusercontent.com/96117491/236533913-9e953c8c-e600-439d-b756-b91ec34b2f78.png)

-> Run the following commands on the Terminal of the VM on ec2 Instance:

<ul>
<li>sudo apt update</li>
<li>sudo apt install nodejs npm git</li>
<li>sudo npm install pm2 -g</li>
</ul>

-> Clone the GitHub Repository on the VM:

![image](https://user-images.githubusercontent.com/96117491/236535779-e9f73753-6cc1-4089-a847-b8afa70b108f.png)

-> Start the pm2 (process manager)

pm2 start npm --name api -- run start:prod  this will start our Node js application named api using pm2 Process  Manager.

![image](https://user-images.githubusercontent.com/96117491/236535663-2794e0a4-c79f-45d4-aca5-850aa9660d31.png)

-> Change Directory to .ssh/ folder and check the authorization keys

![image](https://user-images.githubusercontent.com/96117491/236535974-7a6342a0-a4fc-475f-9d9e-509d6cfceb25.png)

-> Using ssh-keygen we will create public & private keys

![image](https://user-images.githubusercontent.com/96117491/236536111-7dd09c48-5e4f-472a-b79b-42a20fbefa9b.png)

-> Now we must put the public key into the authorized_key

![image](https://user-images.githubusercontent.com/96117491/236536183-186c7aaf-9d75-4c3d-b4c8-d904fd337154.png)

-> Copy the private key and add it as a secret named KEY in GitHub Actions  of our Repository

![image](https://user-images.githubusercontent.com/96117491/236536294-bcff94b6-2ae5-4610-b618-7273fccfe903.png)

-> Similarly add the Secrets for HOST, USER & PORT in GitHub Actions

![image](https://user-images.githubusercontent.com/96117491/236536725-4ebf269e-6cd4-41cc-808a-0e7a328f8cb7.png)

-> On the GitHub Repo after adding the secrets we must re-run the .yml  file

![image](https://user-images.githubusercontent.com/96117491/236536815-05dc961e-531a-4d4d-b83f-4365eb812d08.png)

![image](https://user-images.githubusercontent.com/96117491/236536862-de936093-aa3c-450e-bddc-69e49f55c65b.png)

![image](https://user-images.githubusercontent.com/96117491/236537005-28d9c9ce-5049-4db7-8297-2eb4ea3ed730.png)

-> As the Build and Deploy both are successful, it means that our CICD  pipeline is successfully working and our Nodejs application is live on the  port 8000 of our public IP Address.

![image](https://user-images.githubusercontent.com/96117491/236537062-c5f05ac0-b94f-4f0f-a87a-806b89eed83e.png)

## Conclusion: We have successfully Deployed a CICD pipeline for Nodejs  Application using GitHub Actions & AWS.

ThankYou For Visting Here !!

