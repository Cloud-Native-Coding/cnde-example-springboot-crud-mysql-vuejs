This example code is taken from [Spring Boot CRUD Example with RESTful APIs, JPA, Hibernate, MySQL, Lombok, FreeMarker and VueJS](https://hellokoding.com/full-stack-crud-web-app-and-restful-apis-web-services-example-with-spring-boot-jpa-hibernate-mysql-vuejs-and-docker/)

## Cluster Development

The CNDE runs like a normal Pod within the Kubernetes cluster. Therefore it is possible that all applications you start can be accessed by a Kubernetes Service resource. 

Since this demo exposes port 8888 the Service looks like this:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: product-web-test
spec:
  selector:
    app: code-server
    user-env-name: norbert
  ports:
    - protocol: TCP
      port: 8888
```

(The service' selector points to the running CNDE Pod with the Username `Norbert`)

To test the Web-application we want to create in this demo, we additionally need an Ingress resource to make the service available on the Internet:

```yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  annotations:
    kubernetes.io/ingress.class: nginx
    kubernetes.io/tls-acme: "true"
  name: product-web
spec:
  rules:
  - host: product.norbert.kubeplatform.ch.innoq.io
    http:
      paths:
      - backend:
          serviceName: product-web-test
          servicePort: 8888
        path: /
  tls:
  - hosts:
    - product.norbert.kubeplatform.ch.innoq.io
    secretName: norbert-product-web-tls
```

This can be done for every application, that is running inside your CNDE.


## Step by Step Demo Walkthrough

1. Clone the demo repository with `[git clone https://github.com/Cloud-Native-Coding/cnde-example-springboot-crud-mysql-vuejs.git`

2. In folder `config` execute `k apply -k .` to install required Kubernetes resources
   
3. Install Java
    ```bash
    sudo apt update
    sudo apt install default-jdk
    sudo apt install maven
    ```

4. Install VS-Code extensions: `Java IDE Pack`, `Kubernetes Support`
   
5. Run Application with `mvn clean spring-boot:run`

6. Move Browser to `product.norbert.kubeplatform.ch.innoq.io`

## Demo Walk-through using Docker-Compose

### Install Docker-Compose:

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose up
```

### Use Browser

head again to `product.norbert.kubeplatform.ch.innoq.io`
