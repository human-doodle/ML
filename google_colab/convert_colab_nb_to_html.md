# Convert Google Colab notebook to .html file

I was not able to print(to save as pdf) the notebook while runtime was connected, I had to disconnect inorder to print(to save as pdf). Even so, the pdf wasn't very intuitive.

So, I wanted to export the .ipynb file as .html, but colab only has 2 option: export as .ipynb or .py

I figured out the following method works:

* STEP 1: Download the notebook as .ipynb

* STEP 2: Upload the ipynb file and copy it's path

* STEP 3: in a new cell, run the following code:

```

%%shell
jupyter nbconvert --to html /PATH/TO/YOUR/NOTEBOOKFILE.ipynb

```

NOTE:  The %%shell lets the interpreter know that the following script is interpreted as shell. Don't write anything before %%shell, use a distinct cell for this. 

This creates a new .html file at that location which then can be downloaded.

Source: https://stackoverflow.com/questions/53460051/convert-ipynb-notebook-to-html-in-google-colab
