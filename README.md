Taken from [Spring Boot CRUD Example with RESTful APIs, JPA, Hibernate, MySQL, Lombok, FreeMarker and VueJS](https://hellokoding.com/full-stack-crud-web-app-and-restful-apis-web-services-example-with-spring-boot-jpa-hibernate-mysql-vuejs-and-docker/)


## Preparation Steps

1. Clone the demo repository with `[git clone https://github.com/Cloud-Native-Coding/cnde-example-springboot-crud-mysql-vuejs.git`
2. In folder config execute `k apply -k .` to install required Kubernetes resources

### Install Java

```bash
sudo apt update
sudo apt install default-jdk
sudo apt install mnv
```

1. Install VS-Code extensions: `Java IDE Pack`, `Kubernetes Support`
2. Run Application with `mvn clean spring-boot:run`
3. Move Browser to `product.norbert.kubeplatform.ch.innoq.io`

## same using docker-compose

### Install Docker Compose:

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose up
```

### Use Browser

head again to `product.norbert.kubeplatform.ch.innoq.io`
