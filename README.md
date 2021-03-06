# README for G41

This README is for GPT-2 part of CalvinGAN project
### For GAN training 
https://github.com/genericalexacc/CalvinGAN
### `gpt-2` folder 
`./gpt-2/preprocess.ipynb` <--- notebook to generate train/validate/test dataset <br />
`./gpt-2/requirements.txt` <--- list of dependencies 
`./gpt-2/run_generation.py` <--- script to generate text from gpt-2 <br />
`./gpt-2/run_language_modeling` <--- script to train/evaluate gpt-2 model <br />
`./gpt-2/text_extract.ipynb` <--- notebook to extract text from images dataset <br />
`./gpt-2/text_data.txt` <--- text file generated by `text_extract.ipynb`<br />
`./gpt-2/train.txt` <-- training data set generated from preprocessing script <br />
`./gpt-2/test.txt` <-- testing data set generated from preprocessing script <br />
`./gpt-2/validation.txt` <-- validation data set generated from preprocessing script <br />

### Python environment set up 
```pip install -r requirements.txt```
### Download dataset 
https://drive.google.com/file/d/1weboGcbpHxc7momIMJGddVQs5bKHjWUD/view?usp=sharing
### Run the notebook in this following order
1. text_extract.ipynb
This will give generate a raw text dataset `text_data.txt` from comic panels images dataset
2. preprocessing.ipynb
This note book will generate `train.txt`, `test.txt`, `validation.txt`
### To train gpt-2 model:

This script will create `model` directory.

```python run_language_modeling.py --output_dir=model --model_type=gpt2 --model_name_or_path=gpt2 --do_train --train_data_file=train.txt --do_eval --eval_data_file=valid.txt --per_device_train_batch_size=2 --per_device_eval_batch_size=2 --line_by_line --learning_rate 5e-5 --num_train_epochs=5```


### To generate text:

```python run_generation.py --model_type=gpt2 --model_name_or_path=model --length=300 --prompt="<BOS>" --stop_token="<EOS>" --k=50 --num_return_sequences=10```

Generated texts will be saved in `geenrated_text.txt` <br/>
code reference: https://github.com/itsuncheng/fine-tuning-GPT2 <br/>
https://towardsdatascience.com/fine-tuning-gpt2-for-text-generation-using-pytorch-2ee61a4f1ba7
