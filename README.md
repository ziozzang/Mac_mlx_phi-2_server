# Mac_mlx_phi-2_server
Test server code for Phi-2 model. support OpenAI API spec. using MacOSX system.

Original inference codes are came from https://github.com/ml-explore/mlx-examples/tree/main/phi2

you can use same api with OpenAI API spec.

```
# Install requirements
pip install -r requirements.txt

# Convert Model to MLX format
python convert.py

# Run Server.
python phi2-server.py

# Use anyway.
curl http://localhost:5000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
     "model": "gpt-3.5-turbo",
     "messages": [{"role": "user", "content": "answer why sky is so blue?"}],
     "temperature": 0.5
   }'
```

----

# Phi-2

Phi-2 is a 2.7B parameter language model released by Microsoft with
performance that rivals much larger models.[^1] It was trained on a mixture of
GPT-4 outputs and clean web text.

Phi-2 efficiently runs on Apple silicon devices with 8GB of memory in 16-bit
precision.

## Setup 

Download and convert the model:

```sh 
python convert.py
```

This will make the `weights.npz` file which MLX can read.

## Generate 

To generate text with the default prompt:

```sh
python phi2.py
```

Should give the output:

```
Answer: Mathematics is like a lighthouse that guides us through the darkness of
uncertainty. Just as a lighthouse emits a steady beam of light, mathematics
provides us with a clear path to navigate through complex problems. It
illuminates our understanding and helps us make sense of the world around us.

Exercise 2:
Compare and contrast the role of logic in mathematics and the role of a compass
in navigation.

Answer: Logic in mathematics is like a compass in navigation. It helps
```

To use your own prompt:

```sh
python phi2.py --prompt <your prompt here> --max_tokens <max_tokens_to_generate>
```

To see a list of options run:

```sh
python phi2.py --help
```

[^1]: For more details on the model see the [blog post](
https://www.microsoft.com/en-us/research/blog/phi-2-the-surprising-power-of-small-language-models/)
and the [Hugging Face repo](https://huggingface.co/microsoft/phi-2)
