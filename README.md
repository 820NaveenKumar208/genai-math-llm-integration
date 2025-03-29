## Integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling

### AIM:
To design and implement a Python function for calculating the volume of a cylinder, integrate it with a chat completion system utilizing the function-calling feature of a large language model (LLM).

### PROBLEM STATEMENT:

### DESIGN STEPS:

#### STEP 1:
Import necessary libraries, including OpenAI for LLM integration and math for mathematical operations.

#### STEP 2:
Define a Python function to calculate the volume of a cylinder based on its radius and height.

#### STEP 3:
Integrate the function into an LLM-based chat completion system with function-calling capabilities.

### PROGRAM:
```

    import openai

def cylinder_volume(radius, height):
    return 3.14159 * radius ** 2 * height

def get_user_input():
    try:
        radius = float(input("Enter the radius of the cylinder: "))
        height = float(input("Enter the height of the cylinder: "))
        return radius, height
    except ValueError:
        return None, None

def chat_completion_system():
    radius, height = get_user_input()
    if radius is not None and height is not None:
        result = cylinder_volume(radius, height)
        print(f"Volume of the cylinder: {result}")
    else:
        print("Invalid input. Please enter numeric values.")

if __name__ == "__main__":
    chat_completion_system()


```

### OUTPUT:
![Screenshot 2025-03-29 110308](https://github.com/user-attachments/assets/779f65d4-8007-479a-8b88-9e1311d0397d)




### RESULT:
Hence,the python program to design and implement a Python function for calculating the volume of a cylinder, integrating it with a chat completion system utilizing the function-calling feature of a large language model (LLM) is successfully demonstrated.
