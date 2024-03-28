# Functions with chat models

* [How to call functions with chat models](https://cookbook.openai.com/examples/how\_to\_call\_functions\_with\_chat\_models)

Example in Python for extracting keywords and then applying sentiment analysis of each keyword based on the text they were taken from

````python
```
functions = [
    {
        "name": "sentiment_format",
        "description": "Format output for sentiment evaluation",
        "parameters": {
            "type": "object",
            "properties": {
                "entities": {
                    "type": "array",
                    "description": "Key words extracted from the text",
                    "items": {
                        "type": "object",
                        "properties": {
                            "keyword": {
                                "type": "string",
                                "description": "Key word name",
                            },
                            "sentiment": {
                                "type": "string",
                                "description": "Sentiment towards that key word in the text",
                            },
                            "context": {
                                "type": "object",
                                "description": "Piece of the content that makes this sentiment relevant",
                                "properties": {
                                    "startIndex": { 
                                        "type": "number"
                                
                                    },
                                    "endIndex": {
                                        "type": "number"
                                    }
                                },
                            },
                        },
                    },
                },
            },
            "required": ["keywords"],
        },
    }
    
    ```
def get_sentiments(train_df, text_col: str):
    client = AzureOpenAI(
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),
        api_version="2024-02-01",
        azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    )
    sentiments = []
    system_prompt = "You are a sentiment analysis model that should always call a function to format the output. Focus on <FOCUS>"
    prompt = """
    What is the sentiment of the text towards their main keywords?
    [TEXT]

    """

    for index, row in train_df.iterrows():
        try:
            text = row[text_col]
            id = row["id"]
            system_message = { "role": "system", "content": system_prompt }
            
            formated_prompt = prompt.replace("[TEXT]", text)
            messages = [
                system_message,
                { "role": "user", "content": formated_prompt },
            ]
            sentiment = client.chat.completions.create(model="MODEL NAME", messages=messages, functions=functions)
            sentiments.append((id, sentiment.choices[0].message.function_call.arguments))

        except Exception as e:
            print(e)
            continue
    return sentiments
```
]
```
````
