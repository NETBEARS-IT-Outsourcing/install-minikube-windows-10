# Minikube on Windows 10

## Provider
The tutorial and explanation is also posted on the [NETBEARS](https://netbears.com/blog/install-minikube-windows10/) company blog. You might want to check the website out for more tutorials like this.

## Steps
- Enable Hyper-V from BIOS
- Install Docker for Windows
- Download kubectl + add to path
- Download minikube + add to path
- Configure NEW Hyper-V switch (type = "external")
- Launch docker machine within new hyper-v switch
```
docker-machine create --driver hyperv --hyperv-virtual-switch "EXTERNAL virtual switch" --hyperv-memory 2048  training
``` 
(with "Run as administrator" privileges)
- Connect to docker-machine
```
docker-machine env training | Invoke-Expression
```
- Start minikube cluster with
```
minikube.exe start --kubernetes-version="v1.5.2" --vm-driver="hyperv" --memory=2048 --hyperv-virtual-switch="EXTERNAL virtual switch" --v=7 --alsologtostderr
```
(with "Run as administrator")
- Get minikube and kubectl status
```
minikube status
```

PS :
- If "localkube:Stopped" then :
```
minikube stop
minikube start
```

## Final notes
Need help implementing this?

Feel free to contact us using [this form](https://netbears.com/#contact-form).
