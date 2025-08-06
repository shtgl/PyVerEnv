# Virtual Environments

<div align="justify">
This guide will help you set up a Python virtual environment for your projects, using both the standard `venv`/`pip` method and the modern `uv` tool. These instructions are focused on Windows, but notes for macOS/Linux are included where relevant.
A virtual environment allows to:
<ul> 
<li>Isolate project dependencies</li>
<li>Avoid conflicts between package versions</li>
<li>Reproduce environments easily for development, testing, and deployment</li>
</ul>
</div>

## Pip virtual env

**Prerequisites**
<ul>
<li>Python installed (recommended: 3.8+ for stability, but 3.12+ is supported)</li>
<li>(Optional) Multiple Python versions can be managed by installing them in separate directories</li>
<li>Below setup will focus Windows system. And commands to setup may vary for macOS or Linux</li>
<li>For macOS/Linux, replace backslashes (`\`) with slashes (`/`) and use `source <env_name>/bin/activate` to activate</li>
<li>Always activate your virtual environment before running or installing packages</li>
<li>For projects using Jupyter, install the kernel inside the virtual environment for isolation</li>
<li>Use `uv` for faster installs and modern dependency management, especially for larger projects</li>
</ul>

**Setup**
<div>
1. Create a Virtual Environment

```bash
# Replace <python_path> with your Python executable path
# Example for custom Python install:
C:\Users\<username>\pyver\py3121\python -m venv <env_name>
```
</div>

<div>
2. Activate the Virtual Environment

```bash
# In PowerShell or Command Prompt:
<env_name>\Scripts\activate
```
</div>

<div>
3. Install Project Dependencies

```bash
pip install -r requirements.txt
```
</div>

<div>
4. (Optional) Jupyter Notebook Setup

```bash
pip install jupyter ipython ipykernel
python -m ipykernel install --user --name=<env_name>
# To remove a kernel:
jupyter kernelspec uninstall <env_name>
```
</div>

<div>
5. (Optional) Install Bash Kernel for Jupyter

```bash
pip install bash_kernel
python -m bash_kernel.install
```
</div>

##  UV virtual environment

[`uv`](https://github.com/astral-sh/uv) is a fast Python package/dependency manager and virtual environment tool.

**Setup**
<div>
1. Install uv (globally)

```bash
pip install uv
```
</div>

<div>
2. Create a Virtual Environment

```bash
uv venv <folder_name>
# This creates a .venv directory inside <folder_name>
```
</div>

<div>
3. Activate the Virtual Environment

```bash
<folder_name>\.venv\Scripts\activate
```
</div>

<div>
4. Add or Install Packages

```bash
# To add a package:
uv add <package-name>

# To install from requirements.txt:
uv pip install -r requirements.txt

# To install from pyproject.toml/uv.lock:
uv pip install -e .
```
</div>

<div>
5. Export and Lock Dependencies

```bash
# Export a requirements.txt from uv.lock:
uv export --format requirements-txt

# Create or update a uv.lock file:
uv lock

# Add dependencies from requirements.txt and update uv.lock:
uv add -r requirements.txt
```
</div>

<div>
6. Project Initialization and Advanced uv Usage

```bash
# To initialize a new project (creates pyproject.toml, uv.lock, etc.):
uv init <name-of-project>

# To install packages from requirements.txt:
uv pip install -r requirements.txt

# To install the current project in editable mode:
uv pip install -e .

# To create or update a uv.lock file:
uv lock

# To add dependencies from requirements.txt to pyproject.toml and create/update uv.lock:
uv add -r requirements.txt
```
</div>

## Resources
<ul>
<li><a href="https://www.youtube.com/watch?v=28eLP22SMTA&t=99s">Multiple python installations and virtual env guided video</a></li>
<li><a href="https://docs.python.org/3/library/venv.html">Python venv documentation</a></li>
<li><a href="https://github.com/astral-sh/uv">uv documentation</a></li>
<li><a href="https://docs.jupyter.org/en/latest/">Jupyter documentation</a></li>
</ul>
