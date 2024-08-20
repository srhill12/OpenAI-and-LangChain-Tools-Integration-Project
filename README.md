
# OpenAI and LangChain Tools Integration Project

This project demonstrates the use of LangChain and OpenAI's GPT-3.5-turbo model to create agents capable of using built-in and custom tools to perform tasks like retrieving information from Wikipedia, checking the weather, performing mathematical calculations, and querying APIs.

## Installation

To run this project locally, follow these steps:

1. **Clone the repository:**

   ```bash
   git clone <repository-url>
   ```

2. **Navigate to the project directory:**

   ```bash
   cd your-repo-name
   ```

3. **Create a virtual environment:**

   ```bash
   python3 -m venv env
   ```

4. **Activate the virtual environment:**

   - On Windows:

     ```bash
     .\env\Scripts\activate
     ```

   - On macOS and Linux:

     ```bash
     source env/bin/activate
     ```

5. **Install the required dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

6. **Set up the `.env` file:**

   Create a `.env` file in the project root directory and add your OpenAI and OpenWeather API keys:

   ```bash
   OPENAI_API_KEY=your_openai_api_key
   OPENWEATHER_API_KEY=your_openweather_api_key
   ```

## Usage

After completing the installation steps, you can run the Jupyter Notebook or the Python script to see the agents in action.

### Example Use Cases

1. **Wikipedia Tool Integration:**

   The agent can retrieve information from Wikipedia based on a user query.

   ```python
   query = {"input": "What is the age of the mayor of the capital of Canada?"}
   result = agent.run(query)
   print(result)
   ```

2. **Weather Tool Integration:**

   The agent can check the weather using the OpenWeatherMap API based on a historical or geographical query.

   ```python
   query = {"input": "What is the current weather in the city where penicillin was first isolated?"}
   result = agent.run(query)
   print(result)
   ```

3. **Custom Tool Integration:**

   The agent can perform custom tasks, such as calculating the sum of numbers and querying for interesting facts about them.

   ```python
   query = {"input": 'What is a fun fact about the sum of 22 and 35?'}
   result = agent.run(query)
   print(result)
   ```

## Possible Improvements

- **Expand the Toolset:** Integrate additional tools like translation services, financial data APIs, or social media analysis tools.
  
- **Error Handling:** Improve error handling for the agent to manage unexpected inputs or unavailable services more gracefully.
  
- **User Interface:** Develop a simple web interface for users to interact with the agent using Flask or Streamlit.

- **Performance Optimization:** Implement caching mechanisms or asynchronous processing to enhance the performance of API calls and tool executions.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
```
