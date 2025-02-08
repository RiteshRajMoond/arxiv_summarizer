# ArXiv Paper Summarizer

This project allows you to query research papers from **ArXiv**, extract their metadata, and generate a summarized version of their abstracts using **Hugging Face Transformers**.

## Features

- Fetches research papers from **ArXiv** based on a search query.
- Extracts **title, authors, abstract, categories, and publication date**.
- Uses **Facebook's BART-Large-CNN model** to summarize abstracts.
- Outputs structured data using **Pandas DataFrame**.

## Installation

Run the following command to install dependencies:

```bash
pip install arxiv pandas transformers
Usage
Import necessary libraries:

python
Copy
Edit
import arxiv
import pandas as pd
from transformers import pipeline
Search for Papers:

python
Copy
Edit
query = "AI OR Artificial Intelligence OR Machine Learning"
search = arxiv.Search(query=query, max_results=10, sort_by=arxiv.SortCriterion.SubmittedDate)

papers = []

for result in search.results():
    papers.append({
        'published': result.published,
        "authors": result.authors,
        "title": result.title,
        "abstract": result.summary,
        "categories": result.categories
    })

df = pd.DataFrame(papers)
pd.set_option('display.max_colwidth', None)
print(df.head(10))
Summarize the Abstract:

python
Copy
Edit
summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
abstract = df['abstract'][0]  # Extract first paper's abstract
summarization_result = summarizer(abstract)
print(summarization_result[0]['summary_text'])
Example Output
sql
Copy
Edit
Original Abstract:
[Full abstract of the research paper]

Summarized Abstract:
[Generated summary using BART-Large-CNN]
Requirements
Python 3.x
Google Colab or Jupyter Notebook (Recommended)
Libraries: arxiv, pandas, transformers
How to Run on Google Colab
Open Google Colab.
Upload your script or copy-paste the code.
Run the cells sequentially.
Contributing
Feel free to fork the repository and submit pull requests if you want to improve this project!

License
This project is licensed under the MIT License.

csharp
Copy
Edit

### Instructions to Upload to GitHub
1. Open Google Colab.
2. In a new cell, run:
   ```bash
   !git init
   !git config --global user.name "YourGitHubUsername"
   !git config --global user.email "YourGitHubEmail"
Connect to GitHub:
bash
Copy
Edit
!git remote add origin https://github.com/YourGitHubUsername/YourRepoName.git
Save your file:
bash
Copy
Edit
!echo "# ArXiv Paper Summarizer" > README.md
!git add .
!git commit -m "Initial commit"
!git push origin main
