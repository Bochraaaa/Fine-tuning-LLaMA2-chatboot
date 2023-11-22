# Fine-tuning-LLaMA2-chatboot

# Llama2 Introduction :
Llama 2 was released by Meta in July as a predominantly open-source AI mode
The Llama2 model was introduced in LLaMA: Open Foundation and Fine-Tuned Chat Models, constituting a collection of foundational language models ranging from 7B to 70B parameters, with checkpoints fine-tuned for chat applications. The Llama2 models were trained using bfloat16, but the original inference uses float16. The checkpoints uploaded on the Hub use torch_dtype = 'float16', which the AutoModel API will employ to cast the checkpoints from torch.float32 to torch.float16.

The dtype of the online weights is mostly irrelevant unless you are using torch_dtype="auto" when initializing a model with model = AutoModelForCausalLM.from_pretrained("path", torch_dtype="auto"). The reason is that the model will first be downloaded (using the dtype of the online checkpoints), then it will be cast to the default dtype of torch (becoming torch.float32), and finally, if a torch_dtype is provided in the config, it will be used.

Training the model in float16 is not recommended and is known to produce NaN; therefore, the model should be trained in bfloat16

# Stable Beluga : 
While Stable Beluga 2 is a Llama2 70B model fine-tuned on an Orca-style dataset, this code implements a Stable Beluga variant using distributed training based on Petals' public swarm.

For more information, please visit :
AI Meta Llama : https://ai.meta.com/llama/
Petals : https://github.com/bigscience-workshop/petals/tree/main
Stable Beluga 2: https://huggingface.co/stabilityai/StableBeluga2


