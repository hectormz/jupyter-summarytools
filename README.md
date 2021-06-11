# DataFrame Summary Tools in Jupyter Notebook

This is a python port of `summarytools`,
which is used to generate standardized and comprehensive summary of dataframe in Jupyter Notebooks.

The idea originated from the [`summarytools` R package](https://github.com/dcomtois/summarytools).

* Only `dfSummary` function is made available for now
* Added two html widgets to avoid displaying lengthy content
  * [collapsible summary](#collapsible-summary)
  * [tabbed summary](#tabbed-summary)

## Installation

### Install from repos

1. clone / download this repository
2. Install flit:

    ```bash
    pip install flit
    ```

3. Install package:

    ```bash
    flit install --pth-file .
    ```

### Pip Install

```bash
pip install summarytools
```

## Dependencies

1. python 3.6+
2. packages in [pyproject.toml](./pyproject.toml)

## Quick Start

the quick-start notebook is available in [here](quick-start.ipynb)

out-of-box `dfSummary` function will generate a HTML based data frame summary.

```python
import pandas as pd
from summarytools import dfSummary
titanic = pd.read_csv('./data/titanic.csv')
dfSummary(titanic)
```

![dfSummary](images/dfSummary.png)

## Collapsible summary

```python
import pandas as pd
from summarytools import dfSummary
titanic = pd.read_csv('./data/titanic.csv')
dfSummary(titanic, is_collapsible = True)
```

![collapsible](images/collapsible.gif)

## Tabbed summary

```python
import pandas as pd
from summarytools import dfSummary, tabset
titanic = pd.read_csv('./data/titanic.csv')
vaccine = pd.read_csv('./data/country_vaccinations.csv')
vaccine['date'] = pd.to_datetime(vaccine['date'])

tabset({
    'titanic': dfSummary(titanic).render(),
    'vaccine': dfSummary(vaccine).render()})
```

![tabbed](images/tabbed.gif)

## Export notebook as HTML

when export jupyter notebook to HTML, make sure `Export Embedded HTML` extension is installed and enabled.

![embedded_html](images/embedded_html.png)

Using the following bash command to retain the data frame summary in exported HTML.

```bash
jupyter nbconvert --to html_embed path/of/your/notebook.ipynb
```
