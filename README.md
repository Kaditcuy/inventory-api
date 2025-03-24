# AI-Powered Inventory Management API (FastAPI + GraphQL)

An **AI-driven inventory management API** designed for **manufacturing sales reps and distributors**. Built with **FastAPI, GraphQL, PostgreSQL, and Docker** for high-performance data handling and real-time stock tracking.

---

##  Features
 **FastAPI**: High-speed REST & GraphQL API  
 **GraphQL with Strawberry**: Efficient querying and data retrieval of inventory & orders  
 **PostgreSQL**: Structured, scalable database  
 **Docker**: Easy deployment & containerization  
 **JWT Authentication**: Secure API access  
 **Async Processing**: Real-time stock updates  

---

## Quick Start

### **Clone the Repository**

git clone https://github.com/kaditcuy/inventory-api.git
cd inventory-api

### **Install  dependencies**
pip install -r requirements.txt

### **Start the server**
uvicorn main:app --reload
Server will be running at ```http://localhost:8000```

### ***API Endpoints**
Our API provides both **REST** and **GraphQL** options, allowing users to interact with the inventory system in their preferred way.

---

#### **REST API**
You can interact with the inventory api using standard RESTFUL endpoints

| Method | Endpoint   | Description          |
|--------|-----------|----------------------|
| GET    | /products | Fetch all products   |
| POST   | /products | Add a new product    |
| GET    | /orders   | Get all orders       |
| POST   | /orders   | Place a new order    |

Example **REST Request using cURL**
```sh
curl -X GET "http://localhost:8000/products" -H "accept: application/json"
```
Example **REST Request using Python Requests**
```
import requests

response = requests.get("http://localhost:8000/products")
print(response.json())
```

#### **GraphQL API**
For more flexible queries, use Graphql available through Strawberry at GraphQL Playgrpund on```http://localhost:8000/graphql```

Example **Query using GraphQL Playground**:

```
{
    products{
        id
        name
        stock_level
    }
}
```
Example **GraphQL Request using Python Requests**
```
import requests

url = "http://localhost:8000/graphql"
query = {"query": "{ products { id name stock_level } }"}

response = requests.post(url, json=query)
print(response.json())
```

### **Authentication (JWT)**
To access protected endpoints, obtain a token by sendind a post request to this endpoint 

POST /auth/token

Then include it in headers
Authorization: Bearer <your_token>

### **Running with Docker**
docker-compose up --build

### **🏗 Tech Stack**
* Backend: FastAPI(pyhton)
* Web server: Uvicorn
* Database: PostgreSQL
* API Querying: Graphql(Strawberry)
* Deployment: Docker + Uvicorn
* Authentication: JWT Tokens
* Async Processing: Celery