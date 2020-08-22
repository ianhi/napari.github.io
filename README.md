# napari

### multi-dimensional image viewer for python

[![image.sc forum](https://img.shields.io/badge/dynamic/json.svg?label=forum&url=https%3A%2F%2Fforum.image.sc%2Ftags%2Fnapari.json&query=%24.topic_list.tags.0.topic_count&colorB=brightgreen&suffix=%20topics&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAABPklEQVR42m3SyyqFURTA8Y2BER0TDyExZ+aSPIKUlPIITFzKeQWXwhBlQrmFgUzMMFLKZeguBu5y+//17dP3nc5vuPdee6299gohUYYaDGOyyACq4JmQVoFujOMR77hNfOAGM+hBOQqB9TjHD36xhAa04RCuuXeKOvwHVWIKL9jCK2bRiV284QgL8MwEjAneeo9VNOEaBhzALGtoRy02cIcWhE34jj5YxgW+E5Z4iTPkMYpPLCNY3hdOYEfNbKYdmNngZ1jyEzw7h7AIb3fRTQ95OAZ6yQpGYHMMtOTgouktYwxuXsHgWLLl+4x++Kx1FJrjLTagA77bTPvYgw1rRqY56e+w7GNYsqX6JfPwi7aR+Y5SA+BXtKIRfkfJAYgj14tpOF6+I46c4/cAM3UhM3JxyKsxiOIhH0IO6SH/A1Kb1WBeUjbkAAAAAElFTkSuQmCC)](https://forum.image.sc/tags/napari)
[![License](https://img.shields.io/pypi/l/napari.svg)](https://github.com/napari/napari/raw/master/LICENSE)
[![Build Status](https://api.cirrus-ci.com/github/Napari/napari.svg)](https://cirrus-ci.com/napari/napari)
[![codecov](https://codecov.io/gh/napari/napari/branch/master/graph/badge.svg)](https://codecov.io/gh/napari/napari)
[![Python Version](https://img.shields.io/pypi/pyversions/napari.svg)](https://python.org)
[![PyPI](https://img.shields.io/pypi/v/napari.svg)](https://pypi.org/project/napari)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/napari.svg)](https://pypistats.org/packages/napari)
[![Development Status](https://img.shields.io/pypi/status/napari.svg)](https://github.com/napari/napari)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/python/black)
[![DOI](https://zenodo.org/badge/144513571.svg)](https://zenodo.org/badge/latestdoi/144513571)

**napari** is a fast, interactive, multi-dimensional image viewer for Python. It's designed for browsing, annotating, and analyzing large multi-dimensional images. It's built on top of `Qt` (for the GUI), `vispy` (for performant GPU-based rendering), and the scientific Python stack (`numpy`, `scipy`).

We're developing **napari** in the open! But the project is in an **alpha** stage, and there will still likely be **breaking changes** with each release. You can follow progress on this repository, test out new versions as we release them, and contribute ideas and code.

We're working on [tutorials](https://napari.org/tutorials/), but you can also quickly get started by looking below.

## installation

### from pip, with "batteries included"

napari can be installed on most macOS, Linux, and Windows systems with
Python 3.6, 3.7 and 3.8 using pip:

```sh
pip install napari[all]
```

Note: while not strictly required, it is *highly* recommended to install
napari into a clean virtual environment using an environment manager like
[conda](https://docs.conda.io/en/latest/miniconda.html) or
[venv](https://docs.python.org/3/library/venv.html).  For example, with `conda`:

```sh
conda create -y -n napari-env python=3.8
conda activate napari-env
pip install napari[all]
```

### from source

To clone the repository locally and install in editable mode use

```sh
git clone https://github.com/napari/napari.git
cd napari
pip install -e .[all]

# or, to install in editable mode AND grab all of the developer tools
# (this is required if you want to contribute code back to napari)
pip install -r requirements.txt
```

For more information or troubleshooting see our [installation tutorial](https://napari.org/tutorials/fundamentals/installation)

> ℹ️ **Specifying a GUI Backend**
>
> napari needs a library called [Qt](https://www.qt.io/) to run its user interface
> (UI). In Python, there are two alternative libraries to run this, called
> [PyQt5](https://www.riverbankcomputing.com/software/pyqt/download5) and
> [PySide2](https://doc.qt.io/qtforpython/). By default, we don't choose for you,
> and simply running `pip install napari` will not install either. You *might*
> already have one of them installed in your environment, thanks to other
> scientific packages such as Spyder or matplotlib. If neither is available,
> running napari will result in an error message asking you to install one of
> them.
>
> Running `pip install napari[all]` will install the default framework – currently
> PyQt5, but this could change in the future.
>
> To install napari with a specific framework, you can use:
>
> ```sh
> pip install napari[pyqt5]    # for PyQt5
>
> # OR
> pip install napari[pyside2]  # for PySide2
> ```

## simple example

From inside an IPython shell (started with `ipython --gui=qt`) or jupyter notebook (after running a cell with magic command `%gui qt`) you can open up an interactive viewer by calling

```python
from skimage import data
import napari
viewer = napari.view_image(data.astronaut(), rgb=True)
```

![image](resources/screenshot-add-image.png)

To do the same thing inside a script call

```python
from skimage import data
import napari

with napari.gui_qt():
    viewer = napari.view_image(data.astronaut(), rgb=True)
```

## features

Check out the scripts in our `examples` folder to see some of the functionality we're developing!

**napari** supports six main different layer types, `Image`, `Labels`, `Points`, `Vectors`, `Shapes`, and `Surface`, each corresponding to a different data type, visualization, and interactivity. You can add multiple layers of different types into the viewer and then start working with them, adjusting their properties.

All our layer types support n-dimensional data and the viewer provides the ability to quickly browse and visualize either 2D or 3D slices of the data.

**napari** also supports bidirectional communication between the viewer and the Python kernel, which is especially useful when launching from jupyter notebooks or when using our built-in console. Using the console allows you to interactively load and save data from the viewer and control all the features of the viewer programmatically.

You can extend **napari** using custom shortcuts, key bindings, and mouse functions.

## tutorials

For more details on how to use `napari` checkout our [tutorials](https://napari.org/tutorials/). These are still a work in progress, but we'll be updating them regularly.

## mission, values, and roadmap

For more information about our plans for `napari` you can read our [mission and values statement](./docs/developers/MISSION_AND_VALUES.html), which includes more details on our vision for supporting a plugin ecosystem around napari. We also have
a [roadmap](./docs/developers/ROADMAP_0_3.html) that captures current development priorities within the project.

## contributing

Contributions are encouraged! Please read our [contributing guide](./docs/developers/CONTRIBUTING.html) to get started. Given that we're in an early stage, you may want to reach out on our [Github Issues](https://github.com/napari/napari/issues) before jumping in.

## code of conduct

`napari` has a [Code of Conduct](./docs/developers/CODE_OF_CONDUCT.html) that should be honored by everyone who participates in the `napari` community.

## governance

You can learn more about how the `napari` project is organized and managed from our [governance model](./docs/developers/GOVERNANCE.html), which includes information about, and ways to contact, the [@napari/steering-council](https://github.com/orgs/napari/teams/steering-council) and [@napari/core-devs](https://github.com/orgs/napari/teams/core-devs).

## citing napari

If you find `napari` useful please cite this repository using its DOI as follows:

> napari contributors (2019). napari: a multi-dimensional image viewer for python. [doi:10.5281/zenodo.3555620](https://zenodo.org/record/3555620)

Note this DOI will resolve to all versions of napari. To cite a specific version please find the
DOI of that version on our [zenodo page](https://zenodo.org/record/3555620). The DOI of the latest version is in the badge at the top of this page.

## help

We're a community partner on the [image.sc forum](https://forum.image.sc/tags/napari) and all help and support requests should be posted on the forum with the tag `napari`. We look forward to interacting with you there.

Bug reports should be made on our [github issues](https://github.com/napari/napari/issues/new?template=bug_report.md) using
the bug report template. If you think something isn't working, don't hesitate to reach out - it is probably us and not you!
