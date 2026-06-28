If Kubernetes Services already provide load balancing, why do we need Ingress?
A Service distributes traffic across the Pods behind it using simple load balancing (typically round-robin).
However, a Service has some limitations:
Each application that needs external access often requires its own LoadBalancer Service.
In cloud environments, every LoadBalancer Service usually provisions a separate cloud load balancer, which increases infrastructure cost.
Services don't provide advanced Layer 7 (HTTP/HTTPS) routing such as path-based routing, host-based routing, SSL termination, or URL rewriting.
This is where Ingress becomes valuable.
With a single external Load Balancer and an Ingress Controller, we can:
Route requests based on host names (e.g., app.example.com, api.example.com).
Route requests based on URL paths (e.g., /app, /api).
Configure SSL/TLS termination.
Apply custom routing rules.
Expose multiple Services through a single entry point, reducing cloud costs.
Example
Without Ingress:
Service A → Load Balancer<img width="1536" height="1024" alt="ingress" src="https://github.com/user-attachments/assets/f1ff664b-3e1f-446e-9149-8a6e232a6de2" />
<img width="1536" height="1024" alt="ingress" src="https://github.com/user-attachments/assets/c15e6dad-2164-4780-a6d1-d9fac6b471c1" />

Service B → Load Balancer
Service C → Load Balancer
➡️ Three cloud Load Balancers = Higher cost.
With Ingress:
One external Load Balancer
One Ingress Controller
Multiple backend Services
➡️ A single entry point with advanced routing and lower infrastructure cost.
Understanding Kubernetes isn't just about knowing the components—it's about understanding why they exist and which problems they solve.
Note: Ingress itself doesn't perform load balancing. The Ingress Controller (NGINX, Traefik, AWS Load Balancer Controller, etc.) implements the routing rules defined in the Ingress resource.





