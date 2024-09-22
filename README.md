# fine-tuning-gemma2B on Patient-Doctor Conversational Dataset 
The goal of this finetuning is improve the base model (Gemma 2) to provide better niche answers to medical and health related queries like a doctor would for peculiar aliments.
I picked out Gemma 2 (2 billion parameters) for my base model and quantized its weights using QLoRA. The weights of LLMs are usually saved as bfloat-16 but by employing QLoRA quantization techniques i was able to load in the weight with 4bit precision without losing accuracy.

Fine-tuning the full model will take a lot of time, so to improve the training time, i employed LoRA quantization techniques (LOW Rank Adaptation) which involves attaching an adapter layer with a few parameters. This made entire process faster and more memory-efficient. Instead of training the entire model, i only had to update the parameters of the adapter layers, which accelerated the training process.

I tracked the training process using the Weights & Biases and the finetuning was done on only 1500 examples. I trained for 2 epochs.
