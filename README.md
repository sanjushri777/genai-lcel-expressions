## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:
We need to design a LangChain expression that:

Accepts two dynamic inputs (prompt parameters), such as product and budget, from the user.
Processes the inputs using the LangChain components.
Returns a recommendation based on the input values.
Evaluates the results in a real-world scenario like a product recommendation system.
here i selected Recommender chatbot 
The chatbot or system should recommend products to the user based on their desired product category and budget.

### DESIGN STEPS:


#### STEP 1: Define the Inputs and Create the Prompt Template
Identify your inputs: These are the parameters the user provides, such as a query, preferences, or constraints.
Example: {topic} and {budget}.
Create a prompt template: The prompt uses these inputs to frame the request to the model
#### STEP 2: Choose a Model and Set Up the Output Parser
Select a language model (like OpenAI’s GPT-3, for example) to process the input and generate an output.
Set up an output parser: This will clean or format the model’s raw output to fit the desired structure.

#### STEP 3:Build the Chain and Invoke the Expression
Combine the components into a chain: This sequence connects the prompt, model, and output parser.
Invoke the chain with user inputs and generate the response

### PROGRAM:
```python
import os
import openai
from dotenv import find_dotenv, load_dotenv
from langchain.prompts import ChatPromptTemplate
from langchain.chat_models import ChatOpenAI
from langchain.schema.output_parser import StrOutputParser

_ = load_dotenv(find_dotenv())

openai.api_key=os.environ['OPENAI_API_KEY']



prompt = ChatPromptTemplate.from_template("what is the westher now in {P} .")
model = ChatOpenAI(temperature=1.0)  #adjust the temperature to get creeative response
output_parser = StrOutputParser()

chain = prompt | model | output_parser


product_input = input("ENTER THE PRODUCTS: ")
budget_input = input("ENTER THE BUDGET: ")


result = chain.invoke({"Products": product_input, "budget": budget_input})

print("Recommendation:", result)
```

### OUTPUT:


### RESULT:
