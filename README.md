# open_ai_practice
## Setup Python Environment
### 1. Initialize a New Python Project

#### 1.1. Create a new directory for your project:
```sh
mkdir this-projects-name
cd this-projects-name
```

#### 1.2. Initialize a new Python virtual environment:
```sh
python3 -m venv venv
source venv/bin/activate
```

#### 1.3. Install Flask (a lightweight WSGI web application framework) and requests (for making HTTP requests):
```sh
pip install flask requests
```

### 2. Create the Flask Application
#### 2.1. Create a new file named app.py:

```sh
touch app.py
```

#### 2.2. Open app.py and add the following code:

```python
from flask import Flask, request, jsonify
import requests

app = Flask(__name__)

@app.route('/weather', methods=['POST'])
def get_weather():
    data = request.json
    location = data['location']
    api_key = 'your_api_key'  # Replace with your actual API key
    response = requests.get(f'https://api.weather.com/v3/wx/conditions/current?location={location}&apikey={api_key}')
    return jsonify(response.json())

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

### 3. Run the Flask Application

#### 3.1. In the terminal, run the Flask app:
```sh
python app.py
```
#### 3.2. Your Flask app should now be running. GitHub Codespaces will provide a URL to access your server.


### 4. Test the API Endpoint

#### 4.1. Open a new terminal within the Codespace or use a tool like Postman to test the API endpoint.

<#### 4.2. Make a POST request to the /weather endpoint with a JSON payload, for example:
```sh
curl -X POST http://localhost:5000/weather -H "Content-Type: application/json" -d '{"location": "New York"}'
```

<#### 4.3. You should receive a JSON response with the weather data for New York.



---
### Git Commands
#### 1. Add your changes to the git repository:
```sh
git add .
```

#### 2. Commit your changes:
```sh
git commit -m "Initial commit message"
```

#### 3. Push your changes to GitHub
```sh
git push origin main
```