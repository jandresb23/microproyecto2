*************************************
Upload the model to Docker Hub
*************************************
sudo docker login

-------------------------------------
sudo docker tag <your-image-id> <your-docker-hub-name>/<your-app-name>

sudo docker push <your-docker-hub-name>/<your-app-name>
-------------------------------------

*************************************
Deploy the model to a Kubernetes cluster
*************************************

(Conectarse al clúster - CLI de Azure)

az login

az aks get-credentials --resource-group myResourceGroup --name myAKSCluster


(Conectarse al clúster - PowerShell)

Install-Module -Name Az

Connect-AzAccount
*************************************

kubectl get nodes

kubectl cluster-info


(Implementación de la aplicación)

nano aks-store-quickstart.yaml --> Crear .yaml


(Prueba de la aplicación)

kubectl apply -f aks-store-quickstart.yaml

kubectl expose deployment kubermatic-dl-deployment  --type=LoadBalancer --port 80 --target-port 5000


kubectl get service


*************************************
Probar App desde una terminal:
*************************************
curl -X POST -F "img=@C:\Users\dido0\Desktop\avi1.jpg" http://localhost:5000/predict

*************************************
Probar App en Azure:
*************************************
curl -X POST -F img=@avi1.jpg http://48.211.178.126/predict
curl -X POST -F img=@C:/Users/dido0/Desktop/avi1.jpg http://48.211.178.126/predict