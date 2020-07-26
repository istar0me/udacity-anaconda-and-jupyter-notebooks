# Anaconda

<details><summary>Outline</summary>
<Dropdown Content>

- [Anaconda](#anaconda)
  - [L1.1 Introduction](#l11-introduction)
  - [L1.2 What is Anaconda?](#l12-what-is-anaconda)
    - [Anaconda](#anaconda-1)
    - [Managing Packages](#managing-packages)
    - [Environments](#environments)
    - [Where we go from here](#where-we-go-from-here)
  - [L1.3 Installing Anaconda](#l13-installing-anaconda)
  - [L1.4 Managing packages](#l14-managing-packages)
    - [Install package](#install-package)
      - [Install package without requiring a user prompt](#install-package-without-requiring-a-user-prompt)
      - [Install multiple packages at the same time](#install-multiple-packages-at-the-same-time)
    - [Specify version of package](#specify-version-of-package)
    - [Uninstall packages](#uninstall-packages)
    - [Update packages](#update-packages)
      - [Update all package in environment](#update-all-package-in-environment)
    - [List installed packages](#list-installed-packages)
      - [List installed packages in a named environment](#list-installed-packages-in-a-named-environment)
    - [Search packages](#search-packages)
      - [Search packages with detailed info](#search-packages-with-detailed-info)
    - [Quiz: Which of these commands would you use to install the packages `numpy` and `pandas` with conda? (More than one might be correct - select all that apply.)](#quiz-which-of-these-commands-would-you-use-to-install-the-packagesnumpyandpandaswith-conda-more-than-one-might-be-correct---select-all-that-apply)
  - [L1.5 Managing environments](#l15-managing-environments)
    - [Create an environment](#create-an-environment)
    - [Entering/Leaving an environment](#enteringleaving-an-environment)
    - [Leaving an environment](#leaving-an-environment)
    - [Quiz: What command would you use to create an environment named `data` installed with Python 3.6, numpy, and pandas?](#quiz-what-command-would-you-use-to-create-an-environment-nameddatainstalled-with-python-36-numpy-and-pandas)
  - [L1.6 More environment actions](#l16-more-environment-actions)
    - [Saving and loading environments](#saving-and-loading-environments)
    - [Create an environment from an environment file](#create-an-environment-from-an-environment-file)
    - [Listing environments](#listing-environments)
    - [Removing environments](#removing-environments)
  - [L1.7 Best practices](#l17-best-practices)
    - [Using environments](#using-environments)
    - [Sharing environments](#sharing-environments)
    - [More to learn](#more-to-learn)
  - [L1.8 On Python versions at Udacity](#l18-on-python-versions-at-udacity)
    - [The main breakage between Python 2 and 3](#the-main-breakage-between-python-2-and-3)
  - [Vocabulary](#vocabulary)
  - [Further Reading](#further-reading)

</details>

---

## L1.1 Introduction

- `Anaconda`: distribution of packages built for data science
  - It comes with `conda`, a package and environment manager
- we'll using conda to create environments for isolating projects that use different version of Python and/or different packages
  - tip: we can also use [`Virtualenv`](https://virtualenv.pypa.io/en/latest/) module to setup virtual environments
- we'll also use it to install, uninstall and update packages in our environments

## L1.2 What is Anaconda?

### Anaconda

- `Anaconda` is actually a distribution of software that comes with `conda`, Python, and over 150 scientific packages and their dependencies
- `Anaconda` is a fairly large download (~500 MB) because it comes with the most common data science packages in Python
  - If we don't need all the packages or need to conserve bandwidth or storage space, there is also **`Miniconda`**, a smaller distribution that includes only conda and Python
  - Miniconda can do everything Anaconda does, but doesn't have the preinstalled packages.

### Managing Packages

- Package managers: used to instal libraries and other software
- `pip`: default package manager for Python libraries
- `conda` is similar to `pip`
  - `conda`: available packages are focused around data science
  - `pip`: for general use
- However, `conda` is **not Python specific** like `pip` is, it can also install non-Python packages
- not all Python libraries are available from the `Anaconda` distribution and `conda`. we can (and will) still use `pip` alongside conda to install packages

### Environments

- Along with managing packages, Conda is also a **virtual environment manager**. It's similar to [`virtualenv`](https://virtualenv.pypa.io/en/stable/) and [`pyenv`](https://github.com/yyuu/pyenv), other popular environment managers
- Environments allow us to separate and isolate the packages we are using for different projects
- This issue also happens a lot when dealing with Python 2 and Python 3
- We can also **export** the list of packages in an environment to a file, then include that file with your code
  - This allows other people to easily load all the dependencies for our code. `Pip` has similar functionality with `pip freeze > requirements.txt`

### Where we go from here

1. installing
2. using package manager
3. creating and managing virtual environments

## L1.3 Installing Anaconda

- Download: [Anaconda | Individual Edition](https://www.anaconda.com/products/individual#Downloads)
  - [x] choose Python 3.7
  - [x] choose 64-bit installer

## L1.4 Managing packages

### Install package

- command: `conda install <package_name>`
- e.g. `conda install numpy`
- `Conda` also **automatically installs dependencies**

#### Install package without requiring a user prompt

- It's useful for **scripts**
- command: `conda install -y <packages_name>`
- or `conda install --yes <packages_name>`

#### Install multiple packages at the same time

- command: `conda install <package_name1> <package_name2>`
- e.g. `conda install numpy scipy pandas`

### Specify version of package

- command: `conda install <package_name>=<version>`
- e.g. `conda install numpy=1.10`

### Uninstall packages

- command: `conda remove <package_name>`

### Update packages

- command: `conda update <package_name>`

#### Update all package in environment

- command: `conda update --all`

### List installed packages

- command: `conda list`

#### List installed packages in a named environment

- command: `conda list -n <env_name>`
- or `conda list --name <env_name>`

### Search packages

- command: `conda search '*<package_name>*'`
- e.g. `conda search '*beautifulsoup*'`
  - if we don't add `'`, it will expand the wildcard `*` before running the conda command
    ```
    % conda search *beautifulsoup*  
    zsh: no matches found: *beautifulsoup*
    ```

#### Search packages with detailed info

- command: `conda search <package_name> --info`

### Quiz: Which of these commands would you use to install the packages `numpy` and `pandas` with conda? (More than one might be correct - select all that apply.)

| answer | option                       | reason                                                                                            |
| ------ | ---------------------------- | ------------------------------------------------------------------------------------------------- |
|        | `conda install numpy`        |                                                                                                   |
| (O)    | `conda install pandas`       | Installing `pandas` by itself will also install `numpy` since `numpy` is a dependency of `pandas` |
| (O)    | `conda install numpy pandas` |                                                                                                   |

## L1.5 Managing environments

### Create an environment

- command: `conda create -n <env_name> <list of packages>`
- e.g. create an environment named `my_env` and install `numpy` in it
  - `conda create -n my_env numpy`
- When creating an environment, we can specify which version of Python to install in the environment
  - This is useful when we're working with code in both Python 2.x and Python 3.x
  - Python2 command: `conda create -n py2 python=2`
  - Python3 command: `conda create -n py3 python=3`
- These commands will install the most recent version of Python 3 and 2, respectively
  - To install a specific version, use `conda create -n py python=3.3` for Python 3.3

### Entering/Leaving an environment

- command: `conda activate <env_name>`
- e.g. `conda activate my_env`
- When we're in the environment, we'll see the environment name in the terminal prompt. Something like `(<env_name>) ~ $` / `(my_env) ~ $`

### Leaving an environment

- macOS/Linux command: `conda deactivate`
- Windows command: `deactivate`

> Note: `conda activate` and `conda deactivate` only work on conda 4.6 and later versions. For conda versions prior to 4.6, run `activate` or `deactivate` (on Windows), `source activate` or `source deactivate` (on OSX/Linux)

### Quiz: What command would you use to create an environment named `data` installed with Python 3.6, numpy, and pandas?

| answer | option                                             | reason |
| ------ | -------------------------------------------------- | ------ |
|        | `conda env create -n data python=3.6 numpy pandas` |        |
|        | `conda create data python=3.6 numpy pandas`        |        |
|        | `conda create -n data python=3.6`                  |        |
| (O)    | `conda create -n data python=3.6 numpy pandas`     |        |

## L1.6 More environment actions

### Saving and loading environments

- command: `conda env export > environment.yaml`
  - `conda env export`: write out all the packages in the environment, including the Python version
  - `> environment.yaml`: write the exported text to a YAML file `environment.yaml`

### Create an environment from an environment file

- command: `conda env create -f environment.yaml`
- or `conda env create --file environment.yaml`

### Listing environments

- command: `conda env list`
- asterisk(`*`) next to the environment is the env we're currently using
- The default environment, the environment used when we aren't in one, is called `base`.

```
% conda env list
# conda environments:
#
base                  *  /Users/minidino/opt/anaconda3
py2                      /Users/minidino/opt/anaconda3/envs/py2
py3                      /Users/minidino/opt/anaconda3/envs/py3
```

### Removing environments

- command: `conda env remove -n <env_name>`

## L1.7 Best practices

### Using environments

- having separate environments for Python 2 and Python 3
  - `conda create -n py2 python=2`
  - `conda create -n py3 python=3`
- installed most of the standard data science packages (`numpy`, `scipy`, `pandas`, etc.)
- create environments for each project, it works great for non-data related projects too

### Sharing environments

- it's good practice to make an environment file and include it in the repository
- This will make it easier for people to install all the dependencies for your code
- Tutor also usually include a pip `requirements.txt` file using `pip freeze` ([learn more here](https://pip.pypa.io/en/stable/reference/pip_freeze/)) for people not using conda.

### More to learn

- To learn more about conda and how it fits in the Python ecosystem, check out this article by Jake Vanderplas: [Conda myths and misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/)
- [conda documentation](https://docs.conda.io/projects/conda) we can reference later
- [cheatsheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html) to help us find basic conda commands.

## L1.8 On Python versions at Udacity

### The main breakage between Python 2 and 3

- The place where Python 2 code will fail most often is the `print` statement.

- For most of Python's history including Python 2, printing was done like so:

    ```py
    print "Hello", "world!"
    > Hello world!
    ```

- This was changed in Python 3 to a function.

    ```py
    print("Hello", "world!")
    > Hello world!
    ```

- The `print` function was back-ported to Python 2 in version 2.6 through the `__future__` module:

    ```py
    # In Python 2.6+
    from __future__ import print_function
    print("Hello", "world!")
    > Hello world!
    ```

- The `print` statement doesn't work in Python 3
- If we want to print something and have it work in both Python versions, we'll need to import `print_function` in our Python 2 code.

## Vocabulary

1. mind twisting (adj.) 心靈扭曲的

<!-- ## Reference

1. [title](url) -->

## Further Reading

1. [Conda myths and misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/)
2. [conda documentation](https://docs.conda.io/projects/conda)
3. [cheatsheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)
