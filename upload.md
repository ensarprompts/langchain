Here are prompts for creating an API to deal with file uploads via a runnable:

1. **Prompt for the purpose and scope of the code:**
   ```
   Write a Python script using FastAPI that handles file uploads, processes the files to determine their MIME types, and ingests the files into a vector store. The script should assume the content is a base64 encoded string and should use the LangChain library for processing and vector store integration.
   ```

2. **Prompt for importing necessary libraries and modules:**
   ```
   Import the necessary libraries and modules to handle file uploads using FastAPI, process files using LangChain, and integrate with vector stores. Include `mimetypes`, `os`, `typing`, `UploadFile` from FastAPI, `PGVector`, `Blob`, `ConfigurableField`, `RunnableConfig`, `RunnableSerializable`, `VectorStore` from LangChain, `AzureOpenAIEmbeddings`, `OpenAIEmbeddings`, and `RecursiveCharacterTextSplitter`.
   ```

3. **Prompt for defining a function to guess the MIME type of a file:**
   ```
   Define a function `_guess_mimetype` that takes a file name and file bytes as input and returns the MIME type of the file. The function should use the `mimetypes` library and perform signature-based detection for common file types.
   ```

4. **Prompt for defining a function to convert file uploads to blobs:**
   ```
   Define a function `convert_ingestion_input_to_blob` that takes an `UploadFile` object from FastAPI as input and returns a `Blob` object. The function should read the file data, determine its MIME type using `_guess_mimetype`, and create a `Blob` using the `Blob.from_data` method.
   ```

5. **Prompt for determining whether to use Azure or OpenAI embeddings:**
   ```
   Define a function `_determine_azure_or_openai_embeddings` that checks for the presence of environment variables `OPENAI_API_KEY` or `AZURE_OPENAI_API_KEY` and returns a `PGVector` object configured with the appropriate embeddings. Raise an error if neither environment variable is set.
   ```

6. **Prompt for creating a runnable class for file ingestion:**
   ```
   Create a class `IngestRunnable` that inherits from `RunnableSerializable` and handles the ingestion of files into a vector store. The class should include properties for a text splitter, vector store, assistant ID, and thread ID. Implement the `invoke` method to ingest the blob using a text splitter and vector store, associating documents with either an assistant ID or thread ID.
   ```

7. **Prompt for setting up the database connection string:**
   ```
   Define a constant `PG_CONNECTION_STRING` that constructs the PostgreSQL connection string using environment variables for the host, port, database, user, and password. Use the `connection_string_from_db_params` method from `PGVector`.
   ```

8. **Prompt for configuring and initializing the ingestion runnable:**
   ```
   Initialize an `IngestRunnable` instance with a `RecursiveCharacterTextSplitter` and the determined vector store. Configure the instance to have configurable fields for assistant ID and thread ID using `ConfigurableField`.
   ```

Using these prompts, the comprehensive code for handling file uploads, processing, and ingestion into a vector store can be generated step by step.

## ChatGPT

Original 
https://chatgpt.com/share/6509a7c8-90e0-40fd-acbc-5b80eaf3b8b7

Fix Errors
https://chatgpt.com/share/c9479b5c-b42c-4d98-9d80-461860ece6a5

Recrete again
https://chatgpt.com/share/0451dc0c-c9a4-456c-8b70-8ceec2171d12

Final 1

https://chatgpt.com/share/f9f86f62-96b5-41a5-bd87-7f207b5b190a



