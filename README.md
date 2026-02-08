# CST8915 Lab 2: Full-stack Cloud-native Development

**Student Name**: Joshua Chen
**Student ID**: 041280453
**Course**: CST8915 Full-stack Cloud-native Development
**Semester**: Winter 2026

---

## Demo Video

https://youtu.be/6VuYzqhPg7M

---

## Repositories
https://github.com/JChen-AC/CST8915lab2_store_front
https://github.com/JChen-AC/cst8915lab2_order_service
https://github.com/JChen-AC/CST8915lab2_product_service

---

## Technical Explanations

### What changes did you make to the order-service and product-service to comply with the Configurations and Backing Services factors of the 12-Factor App methodology?

The twelve-factor application’s configuration is defined as “store configuration in the environment” and is also known as externally managed configuration. This means that the configuration values should not be hard-coded or stored in the code-base but instead stored in environment variables. The index.js script was changed to use an .env file, with one being created and storing the RabbitMQ connection string and its port number. It uses the dotenv library and the function “process.env” to get these values from the .env file and uses them in the code. The order-service complies with the configuration factor as it removes the hard-coded values for the port and URL and replaces them with environment variables. The product-service was also changed to use the .env file to store the port number. It uses the dotenv library to load the port number from the .env file and processes it to be used. This makes it comply with the configuration factor as it removes the hard-coded value and replaces it with an environment variable. 

The twelve-factor application’s backing service is defined as “Treat backing services as attached resources”. This means that each individual service should address one another through URLs and be easy to swap out for another service.  This was accomplished through the order-service, treating the RabbitMQ service as a backing service and connecting to it using a connection string. This connection string can easily be changed to another service by swapping the IP address and port number. The product-service uses the backing service because it uses the URL to communicate with the store-front. Both the store-front and product-service use the route “/product” to communicate with the store-front sending a GET request on it and in response returns the product values. As both use a URL to communicate, it is easy for each service to be replaced. The store-front service can easily swap the product-service with something else to change the products that the store has. While the product-service can easily swap the store-front service with something else. 

### Why is it important to use environment variables instead of hard-coding configurations in your application?

It is important to use environment variables to make the application independent of the system on which it was developed. This allows for the application to be run on different systems and devices with minimal changes. Each system might store the application’s dependencies in different locations. This will cause issues when using the hard-coded configurations, as they might not be pointing to the right locations, causing the application to not run properly. Environment variables are variables based on the system, so by using them, you are basically adding system dependent variables into the application. Meaning you only have one location to change these values instead of changing all the instances of the hard-coded configuration in the code. This saves time and ensures that you do not miss an instance when changing the configuration, which could break the application. 

### Why is it important to have separate repositories for each microservice? How does this help maintain independence and scalability of each service?

It is important to have separate repositories for each microservice because it keeps each microservice organized and independent. By separating the code, it keeps each service more organized, as all the related code to that service is in one place. This makes it easier to make changes to the service since you do not have to go looking for all the code related to the service, since it would be in one place. It also makes each service independent, because there will be no dependencies on other services to work, nor would there be code segments in other service portions. Separate repositories also make it easier to scale because you do not have to download unnecessary code. If the code were in a single repository, then you would have to install the whole repository, which would include a lot of unnecessary code for other services, increasing the disk space needed for it. As such, having separate repositories means you only need to download the code for that service, saving space and money. 

---