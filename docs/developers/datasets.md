# Datasets Developer Documentation

- [Cloning a Dataset](#cloning)
- [Testing a Dataset](#testing)
- [Updating a Dataset](#publishing)

## Cloning a Dataset <a name="cloning"></a>

Install [Git Large File Storage (LFS)](https://git-lfs.github.com/):

```bash
git lfs install
```

Clone a repository, e.g. `cannabis_results`:

```bash
git clone https://huggingface.co/datasets/cannlytics/cannabis_results
```

## Testing a Dataset <a name="testing"></a>

You can load the dataset locally for testing with the loading script:

```py
from datasets import load_dataset

# Load the dataset.
dataset = load_dataset('cannabis_results.py', 'ca')
data = dataset['data']
assert len(data) > 0
print('Read %i data points.' % len(data))
```

## Updating the Dataset <a name="publishing"></a>

When you want to make a pull request to a specific dataset, first, create a pull request branch on [Hugging Face](https://huggingface.co), then checkout the branch, e.g.:

```bash
git fetch origin refs/pr/2:pr/2
git checkout pr/2
```

Next, do your modifications and track all of your changes, including any large data files, e.g. `.csv` files:

```bash
git lfs track *.csv
git add *.csv
git commit -m "Added all `.csv` files"
git lfs track *.xlsx
git add *.xlsx
git commit -m "Added all `.xlsx` files"
git lfs track *.zip
git add *.zip
git commit -m "Added all `.zip` files"
git add --all
git status
git commit -m "Updated `cannabis_results` dataset."
```

Finally, make the pull request:

```bash
git push origin pr/x:refs/pr/x
```

🎉 Congratulations, your pull request is now ready to be reviewed and merged by the repository admin!
