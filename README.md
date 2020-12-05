# manGAN


### To train model:

This script will create `model` directory.

```python run_language_modeling.py --output_dir=model --model_type=gpt2 --model_name_or_path=gpt2 --do_train --train_data_file=train.txt --do_eval --eval_data_file=valid.txt --per_device_train_batch_size=2 --per_device_eval_batch_size=2 --line_by_line --learning_rate 5e-5 --num_train_epochs=5```


### To generate text:
```python run_generation.py --model_type=gpt2 --model_name_or_path=model --length=300 --prompt="<BOS>" --stop_token="<EOS>" --k=50 --num_return_sequences=10```
