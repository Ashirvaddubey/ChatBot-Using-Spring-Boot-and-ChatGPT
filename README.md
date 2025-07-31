# ChatBot Using Spring Boot and ChatGPT

A RESTful Spring Boot application that integrates with OpenAI's ChatGPT API to provide intelligent conversational responses. This application serves as a backend service for chatbot functionality, handling message processing and AI-powered responses.

## 🚀 Features

- **RESTful API**: Clean REST endpoints for chat interactions
- **OpenAI Integration**: Seamless integration with ChatGPT API
- **JSON-based Communication**: Standardized request/response format
- **Configurable Model**: Uses GPT-3.5-turbo model with customizable parameters
- **Token Management**: Built-in token usage tracking and limits
- **Spring Boot 3.0.4**: Latest Spring Boot version with Java 17

## 🏗️ Project Structure

```
src/main/java/com/bootcamptoprod/
├── ChatBotUsingSpringBootAndChatGPTApplication.java  # Main application class
├── config/
│   └── ApplicationConfig.java                        # Configuration beans
├── controller/
│   └── ChatGPTController.java                        # REST controller
├── model/
│   ├── common/
│   │   └── Message.java                              # Message model
│   ├── request/
│   │   ├── ChatBotInputRequest.java                  # Input request model
│   │   └── ChatGPTRequest.java                       # OpenAI API request model
│   └── response/
│       ├── ChatGPTResponse.java                      # OpenAI API response model
│       ├── Choice.java                               # Response choice model
│       └── Usage.java                                # Token usage model
└── service/
    └── ChatGPTService.java                           # Business logic service
```

## 🛠️ Technology Stack

- **Java 17**
- **Spring Boot 3.0.4**
- **Spring Web** (RESTful services)
- **Spring Test** (Testing framework)
- **Maven** (Build tool)
- **OpenAI ChatGPT API**

## 📋 Prerequisites

- Java 17 or higher
- Maven 3.6+
- OpenAI API key

## ⚙️ Setup Instructions

### 1. Clone the Repository
```bash
git clone <repository-url>
cd chatbot-using-spring-boot-and-chatgpt-main
```

### 2. Configure OpenAI API Key
Edit `src/main/resources/application.properties`:
```properties
openai.api.key=YOUR_ACTUAL_OPENAI_API_KEY
```

### 3. Build the Application
```bash
mvn clean install
```

### 4. Run the Application
```bash
mvn spring-boot:run
```

The application will start on `http://localhost:8080`

## 🔌 API Documentation

### Chat Endpoint

**POST** `/chat`

Send a message to the chatbot and receive an AI-generated response.

#### Request Body
```json
{
    "message": "Hello, how are you?"
}
```

#### Response
```json
{
    "id": "chatcmpl-1234567890",
    "object": "chat.completion",
    "created": 1677652288,
    "choices": [
        {
            "index": 0,
            "message": {
                "role": "assistant",
                "content": "Hello! I'm doing well, thank you for asking. How can I help you today?"
            },
            "finish_reason": "stop"
        }
    ],
    "usage": {
        "prompt_tokens": 9,
        "completion_tokens": 12,
        "total_tokens": 21
    }
}
```

#### Example Usage with cURL
```bash
curl -X POST http://localhost:8080/chat \
  -H "Content-Type: application/json" \
  -d '{"message": "What is the capital of France?"}'
```

## 🔧 Configuration

### Application Properties
- `openai.api.key`: Your OpenAI API key (required)
- Default model: `gpt-3.5-turbo`
- Default max tokens: `20`

### Customization
You can modify the ChatGPT model and parameters in `ChatGPTService.java`:
```java
chatGPTRequest.setModel("gpt-4");           // Change model
chatGPTRequest.setMax_tokens(100);          // Adjust token limit
```

## 🧪 Testing

Run the test suite:
```bash
mvn test
```

## 📦 Dependencies

The project uses the following main dependencies:
- `spring-boot-starter-web`: Web application support
- `spring-boot-starter-test`: Testing framework
- `spring-boot-maven-plugin`: Maven plugin for Spring Boot

## 🔒 Security Considerations

- Store your OpenAI API key securely
- Consider implementing rate limiting for production use
- Add authentication/authorization for production deployments
- Use HTTPS in production environments

## 🚀 Deployment

### Local Development
```bash
mvn spring-boot:run
```

### Production Build
```bash
mvn clean package
java -jar target/chatbot-using-spring-boot-and-chatgpt-0.0.1-SNAPSHOT.jar
```

### Docker Deployment
```dockerfile
FROM openjdk:17-jdk-slim
COPY target/chatbot-using-spring-boot-and-chatgpt-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🆘 Support

For issues and questions:
- Create an issue in the repository
- Check the OpenAI API documentation for API-related questions
- Review Spring Boot documentation for framework questions

## 🔄 Future Enhancements

Potential improvements for this project:
- Conversation history management
- User session management
- Multiple AI model support
- Response caching
- WebSocket support for real-time chat
- Frontend UI integration
- Database integration for persistent storage
