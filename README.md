# SpringAI Weaviate Vector Demo

This project demonstrates the integration of Weaviate, an open-source vector search engine, with Spring Boot to build a vector store service. The application provides endpoints for loading documents into the Weaviate vector store and searching for similar documents using vector embeddings.

## Prerequisites

Before running the project, ensure you have the following installed:

- **Java 21**: Required to build and run the Spring Boot application.
- **Maven**: Used to build the project.
- **Docker**: Required to run Weaviate in a container.
- **Weaviate Vector Store**: Weaviate is used to store and search vector data.

## Setting Up Weaviate with Docker

Weaviate is a cloud-native, modular search engine that is easy to use with vector embeddings. Follow the steps below to install and run Weaviate using Docker.

### Quick Docker Command to Install Weaviate

Run the following command to start Weaviate:

```bash
docker run -it --rm --name weaviate \
-e AUTHENTICATION_ANONYMOUS_ACCESS_ENABLED=true \
-e PERSISTENCE_DATA_PATH=/var/lib/weaviate \
-e QUERY_DEFAULTS_LIMIT=25 \
-e DEFAULT_VECTORIZER_MODULE=none \
-e CLUSTER_HOSTNAME=node1 \
-p 8080:8080 semitechnologies/weaviate:1.22.4
```

This command will run Weaviate on your local machine, exposing the service on port `8080`.

## Project Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/LegPro/springai-weaviate-vector-demo.git
   cd springai-weaviate-vector-demo
   ```

2. **Configure OpenAI API Key:**

   This project uses OpenAI embeddings for vector generation. Ensure that you have an OpenAI API key and set it in the `application.properties` file:

   ```properties
   spring.ai.openai.api-key=your-openai-api-key
   ```

   Alternatively, you can set the API key as an environment variable:

   ```bash
   export spring.ai.openai.api-key=your-openai-api-key
   ```

3. **Configure Weaviate Connection:**

   In the `application.properties` file, make sure the Weaviate connection details are configured properly:


4. **Run the Application:**

   You can run the Spring Boot application using Maven:

   ```bash
   mvn spring-boot:run
   ```

   The application will be running on port `9090`.

5. **Endpoints:**

    - **Load Documents**: Load vectorized documents into the Weaviate vector store.
      ```bash
      GET http://localhost:9090/load
      ```

    - **Search Documents**: Search for similar documents based on a vector query.
      ```bash
      GET http://localhost:9090/search?query=<your-search-query>
      ```

The controller provides two endpoints: one for loading documents into the Weaviate vector store and another for searching for documents based on a query.
