## NAME : NAVEEN KUMAR T
## REG NO : 212223220067
## Integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling

### AIM:
To integrate mathematical calculations with a Chat Completion System using LLM Function-Calling by building a Python program that calculates the volume of a sphere based on user queries. The system uses OpenAI’s function-calling capability to connect natural language requests with precise mathematical computations.



### DESIGN STEPS:

#### STEP 1:
Import necessary libraries:
os and dotenv → to securely load the OpenAI API key.
openai → for Chat Completion with function-calling.
json → to handle structured input and output.

#### STEP 2:
Define a Python function (sphere_volume) that calculates the volume of a sphere using the formula:
V=4/3​πr3

#### STEP 3:
Describe the function schema (name, description, and parameters) and pass it to the LLM as a tool. This tells the model how and when to call the Python function.

#### STEP 4:
Simulate a conversation by creating a user query such as:
“What is the volume of a sphere with radius 5 meters?”

#### STEP 5: 
Check if the LLM requests a function_call

#### STEP 6
Print the final result, which provides an accurate mathematical answer expressed in natural language.

### PROGRAM:
```

import os
import json
import openai
from dotenv import load_dotenv

# 🔹 Load API key from .env
load_dotenv()
openai.api_key = os.getenv("OPENAI_API_KEY")


def sphere_volume(radius: float) -> str:
    """
    Calculate the volume of a sphere given its radius.
    Formula: V = 4/3 * π * r³
    """
    pi = 3.141592653589793
    volume = (4 / 3) * pi * (radius ** 3)
    return json.dumps({"radius": radius, "volume": volume})

tools = [
    {
        "name": "sphere_volume",
        "description": "Find the volume of a sphere based on its radius.",
        "parameters": {
            "type": "object",
            "properties": {
                "radius": {
                    "type": "number",
                    "description": "Radius of the sphere in meters."
                }
            },
            "required": ["radius"]
        }
    }
]


messages = [
    {"role": "user", "content": "What is the volume of a sphere with radius 5 meters?"}
]

response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=messages,
    functions=tools
)

response_message = response["choices"][0]["message"]


if "function_call" in response_message:
    fn_args = json.loads(response_message["function_call"]["arguments"])
    result = sphere_volume(**fn_args)

    # Append function response to chat history
    messages.append({
        "role": "function",
        "name": "sphere_volume",
        "content": result,
    })

    final_response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=messages
    )

    print(final_response["choices"][0]["message"]["content"])#T.NaveenKumar_212223220067


```

### OUTPUT:
<img width="1640" height="279" alt="Screenshot 2025-09-19 110225" src="https://github.com/user-attachments/assets/e1367e6a-9d8e-4c85-b644-408714157e76" />




### RESULT:
Hence, the Python program to design and implement a function for calculating the volume of a sphere, and its integration with a chat completion system utilizing the function-calling feature of a Large Language Model (LLM), is successfully demonstrated.
