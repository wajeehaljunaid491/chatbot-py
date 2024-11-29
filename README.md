Get started
Clone the repository
git clone https://github.com/wajeehaljunaid491/chatbot-py.git
Corpus
In the corpus file, the input-output sequence pairs should be in the adjacent lines. For example,

I'll see you next time.
Sure. Bye.
How are you?
Better than ever.
The corpus files should be placed under a path like,

pytorch-chatbot/data/<corpus file name>
Otherwise, the corpus file will be tracked by git.

Pretrained Model
The pretrained model on movie_subtitles corpus with an bidirectional rnn layer and hidden size 512 can be downloaded in this link. The pretrained model file should be placed in directory as followed.

mkdir -p save/model/movie_subtitles/1-1_512
mv 50000_backup_bidir_model.tar save/model/movie_subtitles/1-1_512
Training
Run this command to start training, change the argument values in your own need.

python main.py -tr <CORPUS_FILE_PATH> -la 1 -hi 512 -lr 0.0001 -it 50000 -b 64 -p 500 -s 1000
Continue training with saved model.

python main.py -tr <CORPUS_FILE_PATH> -l <MODEL_FILE_PATH> -lr 0.0001 -it 50000 -b 64 -p 500 -s 1000
For more options,

python main.py -h
Testing
Models will be saved in pytorch-chatbot/save/model while training, and this can be changed in config.py.
Evaluate the saved model with input sequences in the corpus.

python main.py -te <MODEL_FILE_PATH> -c <CORPUS_FILE_PATH>
Test the model with input sequence manually.

python main.py -te <MODEL_FILE_PATH> -c <CORPUS_FILE_PATH> -i
Beam search with size k.

python main.py -te <MODEL_FILE_PATH> -c <CORPUS_FILE_PATH> -be k [-i] 
