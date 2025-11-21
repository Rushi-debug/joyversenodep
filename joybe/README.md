# Joyverse Backend Server

## Environment Setup

### 1. Environment Variables

Copy the `.env.example` file to `.env` and update the values:

```bash
cp .env.example .env
```

### 2. Required Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `JWT_SECRET` | Secret key for JWT token signing | `your_super_secure_jwt_secret_key_here` |
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/joyverse` |
| `PORT` | Server port (optional, defaults to 3002) | `3002` |
| `NODE_ENV` | Environment mode | `development` or `production` |

### 3. JWT Secret Key Security

**IMPORTANT**: The JWT secret key should be:
- At least 32 characters long
- Contain a mix of letters, numbers, and special characters
- Be unique for each environment (development, staging, production)
- Never be committed to version control

Example of a strong JWT secret:
```
JWT_SECRET=joyverse_2024_super_secure_random_key_with_numbers_123_and_symbols_!@#
```

### 4. MongoDB Setup

#### Local MongoDB:
```
MONGODB_URI=mongodb://localhost:27017/joyverse
```

#### MongoDB Atlas (Cloud):
```
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/joyverse?retryWrites=true&w=majority
```

### 5. Starting the Server

```bash
# Development mode with auto-restart
npm run dev

# Production mode
npm start
```

### 6. Security Notes

- The `.env` file is automatically ignored by git
- Never share your JWT secret key
- Use different JWT secrets for different environments
- Regularly rotate JWT secrets in production

## API Endpoints

### Authentication
- `POST /api/login` - Login with JWT token response

### Protected Routes
All routes that require authentication should include the JWT token in the Authorization header:
```
Authorization: Bearer <your_jwt_token>
```

## JWT Token Structure

The JWT token contains:
```json
{
  "id": "user_id",
  "username": "username",
  "role": "admin|superadmin|user",
  "adminId": "admin_id_for_children",
  "exp": "expiration_timestamp"
}
```-->First we have to save key value pair .pam file in desktop in AWS folder
-->open cmd in this directory
-->now paste the ssh key which was copied from aws instance and click enter
then run following commands
-->sudo apt update
-->sudo apt-get install docker.io
-->sudo apt install git
-->sudo apt install nano
now in desktop create a folder Example in that create simple index.html  with any <h> and <p> tags
push the index.html to git 
After pushing clone the repo url

Run the following commands
-->git clone url
-->ls
you can see ur repo directory 
-->cd yourdir
-->ls
you will see index.html
-->nano Dockerfile
then paste the following to dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
-->press ctrl+o and enter then ctrl+x to exit
-->sudo  docker build -t myweb .
-->sudo  docker run -d -p 80:80 myweb
then click public ipv4 in the instance go and access in browser...


if maven project then the docker file would be
FROM tomcat:9-jdk11
COPY target/* .war /usr/local/tomcat/webapps/


1)Kubernetes
(docker on lo pettu)




kubectl version --client
minikube start


kubectl create deployment mynginx --image=nginx

if already created then 
kubectl set image deployment/myngnix nginx=nginx:latest

kubectl get deployments

Check the following commands:
kubectl get pods
kubectl describe pods


kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80


kubectl scale deployment mynginx --replicas=4
kubectl get service myngnix

kubectl port-forward svc/mynginx 8081:80
Access the app via http://localhost:8081.


If Error, use this option, Using Minikube Tunnel:
o	Start the tunnel:
minikube tunnel
o	Retrieve the service URL:
minikube service mynginx --url
o	Open the provided URL in your browser.


Minikube dashboard

kubectl delete deployment mynginx
kubectl delete service mynginx

minikube stop

minikube delete





2)Nagios(docker on lo pettu)


docker pull jasonrivers/nagios:latest
docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios:latest

Open your browser and navigate to:
http://localhost:8888
o	Login Credentials:
	Username: nagiosadmin
	Password: nagios


docker stop nagiosdemo

docker rm nagiosdemo

docker images

docker rmi jasonrivers/nagios:latest

Token expires after 24 hours.
