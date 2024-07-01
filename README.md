# eCommerce-System-Platform-on-Google-Cloud-Platform

**Features:**
1. **User-friendly ticket creation and management.**
2. **Microservices architecture for scalability and modularity.**
3. **Docker containers for consistent deployment environments.**
4. **GKE (Google Kubernetes Engine) orchestration for scaling and management.**
5. **Google Cloud Load Balancing for routing and load balancing.**

**Technologies:**
- **Node.js:** Backend development.
- **React.js (Next.js):** Frontend user interface.
- **Docker:** Containerization of microservices.
- **Google Kubernetes Engine (GKE):** Container orchestration.
- **Google Cloud Load Balancing:** Load balancing.

**Getting Started:**

Follow these instructions to set up and run the project locally for development or testing purposes. Make sure you have Docker and GKE installed.

1. **Clone the repository:**
   ```bash
   git clone https://github.com/edsphinx/ecommerce-microservices.git
   ```
2. **Navigate to the project folder:**
   ```bash
   cd e-commerce-microservices
   ```
3. **Set up GKE:**
   - Create a GKE cluster:
     ```bash
     gcloud container clusters create e-commerce-cluster --num-nodes=3
     ```
   - Deploy the application to the GKE cluster:
     ```bash
     kubectl apply -f k8s/
     ```
4. **Configure Google Cloud Load Balancing:**
   - Set up an Ingress resource in GKE:
     ```yaml
     apiVersion: networking.k8s.io/v1
     kind: Ingress
     metadata:
       name: ecommerce-ingress
     spec:
       rules:
       - host: ecommerce.yourdomain.com
         http:
           paths:
           - path: /
             pathType: Prefix
             backend:
               service:
                 name: e-commerce-service
                 port:
                   number: 80
     ```
   - Apply the Ingress resource:
     ```bash
     kubectl apply -f ingress.yaml
     ```

**Architecture:**
The project follows a microservices architecture to ensure scalability, modularity, and maintainability. Docker containers encapsulate each microservice, and GKE manages container orchestration.

**Microservices Architecture:**
- **User Service:** Handles user authentication and management.
- **Product Service:** Manages product catalog and details.
- **Order Service:** Processes and manages customer orders.
- **Payment Service:** Handles payment processing and transactions.
- **Notification Service:** Manages user notifications and communications.

**Explanation of the Microservices Architecture:**
1. **User Service:** Interacts with a managed database service like Google Cloud SQL or Firestore for user data.
2. **Product Service:** Stores product information in Google Cloud SQL or Firestore.
3. **Order Service:** Manages order details and state, communicating with the Payment Service and Notification Service.
4. **Payment Service:** Integrates with external payment gateways, ensuring secure transactions.
5. **Notification Service:** Sends email/SMS notifications using services like SendGrid or Twilio.

Each microservice runs in its own Docker container, managed by GKE. The Google Cloud Load Balancing service ensures efficient routing and load balancing, providing a scalable and reliable eCommerce platform.

**Conclusion:**
By leveraging GCP-specific tools and services, this alternative eCommerce system platform ensures enhanced scalability, efficiency, and ease of management while maintaining a robust and modular architecture.

