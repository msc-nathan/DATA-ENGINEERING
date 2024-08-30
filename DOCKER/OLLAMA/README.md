## MSC/OLLAMA

### Build image from docker file
```sh
docker build -t msc/ollama .
```
### Run docker from image msc/ollama
```sh
docker run -it -d --name ollama-server --hostname ollama-server --restart=always -p 11434:11434 msc/ollama
```
### Download llm model
```sh
ollama pull llama3.1:8b 
```
### Run model
```sh
ollama run llama3.1:8b
```

### API
```sh
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.1",
  "prompt":"Why is the sky blue?"
}'

curl http://localhost:11434/api/chat -d '{
  "model": "llama3.1",
  "messages": [
    { "role": "user", "content": "why is the sky blue?" }
  ]
}'

```

### Ollama/Ollama Docker Image Run CPU
```sh
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

### Ollama/Ollama Docker Image Run GPU
```sh
docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```