# Fine-Tuning LLaMA 2 7B with QLoRA on Guanaco Dataset

This project fine-tunes the [NousResearch/Llama-2-7b-chat-hf](https://huggingface.co/NousResearch/Llama-2-7b-chat-hf) model using QLoRA on the [mlabonne/guanaco-llama2-1k](https://huggingface.co/datasets/mlabonne/guanaco-llama2-1k) dataset. The resulting model demonstrates strong performance on instruction-following tasks, with efficient GPU memory usage through 4-bit quantization.

---

## Model Overview

- **Base Model**: LLaMA 2 7B Chat (`NousResearch/Llama-2-7b-chat-hf`)
- **Adapter Method**: LoRA with QLoRA (4-bit quantization)
- **Dataset**: Guanaco (1,000 instruction-response pairs)
- **Training Framework**: Hugging Face Transformers + PEFT + bitsandbytes
- **Hardware Used**: T4 GPU via Google Colab

---

## Setup and Configuration

### LoRA & Quantization Settings
- LoRA rank (`r`): 64  
- LoRA alpha: 16  
- Dropout: 0.1  
- 4-bit Quantization: Enabled  
- Quant type: nf4  
- Compute dtype: float16

### Training Hyperparameters
- Epochs: 1  
- Learning rate: 2e-4  
- Batch size: 4  
- Optimizer: paged_adamw_32bit  
- Scheduler: cosine  
- Gradient checkpointing: Enabled  
- Warmup ratio: 0.03

---

## Training Results

| Step | Training Loss |
|------|----------------|
| 25   | 1.7867         |
| 50   | 0.8954         |
| 75   | 0.8269         |
| 100  | 0.9502         |
| 125  | 0.8806         |
| 150  | 0.9289         |
| 175  | 0.8719         |
| 200  | 0.7994         |
| 225  | 0.7870         |
| 250  | 0.8751         |

- **Final Training Loss**: 0.9602  
- **Total Training Time**: ~25.9 minutes  
- **Training Throughput**: 0.644 samples/sec, 0.161 steps/sec  
- **FLOPs used**: 2.04e+16

