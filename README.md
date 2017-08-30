# Data Science Notebooks
A number of notebooks showing practical examples of data science


This repository is a work in progress, more notebooks will be added in the future.

## Notebooks

Each of these notebooks has a different focus; here is a list of the notebooks and their main topic.

- Customer Churn: How to predict customer churn, using a telecom dataset; focus on systematical model evaluation.

- Plot.ly: A few examples of interactive charts using the `plotly` library; main focus in on data visualization. Watch it with interactive charts [here](http://nbviewer.jupyter.org/github/asolda/data_science_notebooks/blob/master/plotly.ipynb).

- Seaborn: Another data visualization notebook, after a brief overview of the `seaborn` library there is a practical example on a marathon dataset.

- Time Series: Analysis of time series using `statsmodel` for data exploration (auto-correlation, partial ac, decomposition) and `seaborn` for visualization, using a stock price dataset.

- Titanic: The famous Titanic challenge from Kaggle; include data visualization, data exploration, feature engineering and model evaluation.

## Docker container

You can run all the notebooks in the provided Docker container; this can be extremely useful if you have troubles configuring your environment or if you want to quickly try these notebooks without messing up your laptop.

You can build the image with the provided Dockerfile (`docker build docker/` from the root of the project) or you can pull the container from [my dockerhub profile](https://hub.docker.com/r/asolda/data_science_notebooks/).

To start the container, simply run `docker run -it --rm -p 8888:8888 asolda/data_science_notebooks`. Take note of the authentication token included in the notebook startup log messages. Include it in the URL you visit to access the Notebook server or enter it in the Notebook login form.

The container itself is a modified version of the [jupyter datascience container](https://github.com/jupyter/docker-stacks/tree/master/datascience-notebook), I've just removed some packages that I don't use and I have included a few more packages that I use (such as plotly and cufflinks).

### Notebook options

The Docker container executes a `start-notebook.sh` script script by default. You can pass Jupyter command line options through this script when launching the container, for example you can disable all authentication mechanisms:
```
docker run -d -p 8888:8888 asolda/data_science_notebooks start-notebook.sh --NotebookApp.token=''
```

Furthermore, the `start.sh` script supports the same features as the default start-notebook.sh script, but allows you to specify an arbitrary command to execute; as an example, to run JupyterLab instead of the classic notebook, run the following:
```
docker run -it --rm -p 8888:8888 asolda/data_science_notebooks start.sh jupyter lab
```
