# CSCI-566 Assignment 1

## The objectives of this assignment
* Implement the forward and backward passes as well as the neural network training procedure
* Implement the widely-used optimizers and training tricks including dropout
* Implement recurrent neural networks from scratch
* Use recurrent neural networks for language modeling of arbitrary text corpora

## Work on the assignment
Working on the assignment in a virtual environment is highly encouraged.
In this assignment, please use Python `3.6`.
You will need to make sure that your virtualenv setup is of the correct version of python.

Please see below for executing a virtual environment.
```shell
cd csci566-assignment1
pip3 install virtualenv # If you didn't install it

# replace your_virtual_env with the virtual env name you want
virtualenv -p $(which python3) your_virtual_env
source your_virtual_env/bin/activate

# install dependencies
pip3 install -r requirements.txt
# or
pip3 install numpy jupyter ipykernel opencv-python matplotlib

# work on the assignment
deactivate # Exit the virtual environment
```

## Work with IPython Notebook
To start working on the assignment, simply run the following command to start an ipython kernel.
```shell
# add your virtual environment to jupyter notebook
source your_virtual_env/bin/activate
python -m ipykernel install --user --name=your_virtual_env

# port is only needed if you want to work on more than one notebooks
jupyter notebook --port=your_port_number

```
and then work on each problem with their corresponding `.ipynb` notebooks.
Check the python environment you are using on the top right corner.
If the name of environment doesn't match, change it to your virtual environment in "Kernel>Change kernel".

## Problems
In each of the notebook file, we indicate `TODO` or `Your Code` for you to fill in with your implementation.
Majority of implementations will also be required under `lib` with specified tags.

### Problem 1: Basics of Neural Networks (40 points)
The IPython Notebook `Problem_1.ipynb` will walk you through implementing the basics of neural networks.

### Problem 2: RNNs for Language Modeling (60 points)
The IPython Notebook `Problem_2.ipynb` will walk you through implementing a recurrent neural network (RNN) from scratch and using it for language modeling.

## How to submit

Run the following command to zip all the necessary files for submitting your assignment. Note that, in addition to your notebook **with all cell outputs** you will need to manually create a submission PDF for each problem set that compiles all generated plots / answers. Detailed instructions are at the end of the notebooks. The command below aggregates all notebooks and solution PDFs.

```shell
sh collectSubmission.sh
```

This will create a file named `assignment1.zip`, **please rename it with your usc student id (eg. 4916525888.zip)**, and submit this file through the [Google form](https://forms.gle/uP9TD8T6FkUBLufZ6).
Do NOT create your own .zip file, you might accidentally include non-necessary materials for grading.
We will deduct points if you don't follow the above submission guideline.

**!! SUBMIT YOUR NOTEBOOK INCLUDING ALL CELL OUTPUTS, WE WILL NOT RERUN YOUR NOTEBOOKS !!**

## Questions?
If you have any question or find a bug in this assignment (or even any suggestions), we are more than welcome to assist through Piazza.

Again, NO INDIVIDUAL EMAILS WILL BE RESPONDED.

PLEASE USE **PIAZZA** TO POST QUESTIONS (under folder assignment1).

## FAQ

- **Cannot get 50% accuracy for TinyNet in Problem 1**\
You can try to vary the batch size, epochs and learning rate decay. Please don't modify any code outside the TODO block.

- **What is a good starting learning rate?**\
There is a good article: https://medium.com/octavian-ai/which-optimizer-and-learning-rate-should-i-use-for-deep-learning-5acb418f9b2

- **My RNN in Problem 2 is better than the LSTM?** \
Try experimenting with the number of training epochs (LSTM may train slower in the beginning) and the training prediction horizon (benefits of LSTMs get more apparent on longer prediction problems). \
Even then, it is possible that the training dataset is too simple to show large benefits of LSTMs.

- **When parsing the text data file for Problem 2 I get a `charmap codec can't decode` error.**\
This might be a platform dependent issue. In past years adding `encoding="utf8"` to the file `open` command helped in these cases.

- **What is the `meta` variable used for in Problem 2?**\
This variable is used to pass all values to the backward pass that are necessary to compute the gradients. You can use it as a dictionary to pass any desired values over to the `backward` function.

- **I experimented with the hyperparameters and tried many different combinations, which ones should I report?**\
The usual rule of thumb is to report results with the best hyperparameters you found. \
Exception is the prediction horizon parameter `T` in Problem 2, please **do not** report results for `T` smaller than the default value.

- **Am I allowed to change code outside the TODO blocks?**\
Unless specified otherwise (eg for hyperparameters) please do not change any code outside TODO blocks.

- **My %reload_ext autoreload command does not work, how to fix it?**\
This has been observed in the past and, whenever it was a problem, could be fixed by downgrading IPython to version 7.5.0: `pip3 install ipython==7.5`.

- **The zip file to submit is too large**\
Make sure you do not include your virtual environment, checkpoints, or datasets.

- **The submission script is not working on Windows machines**\
Try installing the `zip` package through `cygwin`.

- **How can I update my submission before the deadline?**\
You can submit your solution up to 10 times **before the deadline** without penalty. You do not need to remove any submitted files but can simply make another submission, we will only grade your latest submission. If you make a submission **after the deadline** we will still grade your latest submission, but deduct late days accordingly.

- **General debugging tips**
1. Make sure your implementations matches the specified model layers perfectly.
2. Put print statements at various places inside your implementation code to make sure every module is working as it should. 
(but please remove any additional print statements for submission)

