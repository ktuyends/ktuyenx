---
title: "Python Modules and Environments"
layout: single-sidebar
date: "2021-12-08"
publishDate: "2021-12-08"
lastUpdated: "2021-12-08"
slug: python-invironement
subtitle: ""
summary: "Một trong những hướng dẫn đầu tiên khi học Python là hãy tải Python từ trang web của nó và cài đặt trên hệ điều hành của mình. Nếu bạn là một người mới làm quen với Python..."
categories:
  - Blog
  - Python
featured: yes
---

<p style="text-align:justify">Một trong những hướng dẫn đầu tiên khi học Python là hãy tải Python từ trang web của nó và cài đặt trên hệ điều hành của mình. Nếu bạn là một người mới làm quen với Python thì bạn sẽ không cần quan tâm quá nhiều đến các phiên bản được cài đặt trên máy tính. </p>

<p style="text-align:justify">Tuy nhiên, khi chúng ta làm việc với nhiều dự án, mỗi dự án lại dựa trên một phiên bản Python và có các package đi kèm khác nhau. Việc thay đổi các phiên bản đôi lúc làm chương trình không thể thực thi như mong muốn. Hoặc đôi khi trên máy của chúng ta có quá nhiều phiên bản và chúng ta không biết phiên bản hiện tại là phiên bản nào, được cài đặt ở đâu.</p> 

<p style="text-align:justify">Vì vậy, lời khuyên là với mỗi dự án nên dựa trên một phiên bản Python riêng. Trong bài viết này, mình sẽ giới thiệu một số thư viện giúp giải quyết vấn đề này.</p>

## 1. Tạo môi trường với Conda

Đầu tiên, các bạn vào trang [Miniconda](https://docs.conda.io/en/latest/miniconda.html), download và cài đặt phiên bản tương ứng với máy tính. Sau khi cài đặt xong cần thêm Miniconda vào Path, với Windows thì link sẽ là: `C:\Users\ktuyends\miniconda3\Scripts`

Bật Window PowerShell lên và chạy các lệnh sau để thêm Conda và update:

```bash
conda init
conda config --set auto_activate_base false
conda update --all
conda config --add channels conda-forge
```

### 1.1. Một số câu lệnh làm việc với môi trường bằng Conda

```bash
# Tạo environment
conda create -n env_name python=<version>

# Activate
conda activate env_name

# Deactivate
conda deactivate
```

```bash
# Xem list các environment hiện có
conda info --env

# Xóa environment
conda remove --name env_name --all

# Clone từ myenv
# Tạo environment từ một environment đã có
conda create --name myclone --clone myenv

# export các thư viện trong env
conda active env_name
conda env export > environment.yaml
conda env create -f environment.yaml # từ env khác
```

### 1.2. Tìm kiếm, cài đặt và xóa package bằng Conda

```bash
# Tìm package
conda search pack_name

# Cài đặt
conda install pack_name=<version>

# Xóa
conda remove pack_name
```

## 2. Quản lý Package với PIP

### 2.1. Một số câu lệnh PIP

```bash
# Xem danh sách các packages được cài đặt
pip list

# Cài đặt package
pip install pack_name

# Xóa package 
pip uninstall pack_name

# Update 
pip install -U pack_name

# Xem một package được cài đặt ở đâu
pip show pack_name

# Cài đặt pack_age cho một phiên bản Python nào đó
python3 -m pip install pack_name
```

### 2.2. Danh sách các package được cài đặt

```bash
# Xem danh sách các package và phiên bản
python -m pip freeze

# Tạo danh sách file các package
python -m pip freeze > requirements.txt

# Cài đặt trên một môi trường khác
python -m pip install -r requirements.txt
```

## 3. Pyenv và Poetry

Với những người làm dữ liệu như Data Analyst hoặc Data Scientist, họ thường sẽ có xu hướng sử dụng `conda` đi kèm với Anaconda. Nếu bạn không thích `conda` thì có thể sử dụng `Pyenv` và `Poetry`, trong đó:

- **Pyenv**: giúp quản lý và cài đặt các phiên bản Python.
- **Poetry**: giúp tạo environment, quản lý và cài đặt các thư viện _(packages, modules)_ cho từng dự án.

### 3.1. Cài đặt Pyenv trên Windows

Đầu tiên chúng ta vào trang web _[Pyenv-win](https://github.com/pyenv-win/pyenv-win)_, tải xuống repository và giải nén. Sau đó đọc hướng dẫn cài đặt _[Installation](https://github.com/pyenv-win/pyenv-win#installation)_ và làm theo. 

### 3.2. Một số câu lệnh với pyenv

```bash
# Xem tất cả các phiên bản có sẵn
pyenv install --list

# Cài đặt một phiên bản
pyenv install <version>

# Xem các phiên bản được cài đặt bởi pyenv
pyenv versions

# Chỉ định global version
pyenv global <version>
```

### 3.3. Cài đặt Poetry trên Windows

Các bạn vào trang web _[python-poetry](https://python-poetry.org/docs/#installation)_ để xem cách cài đặt Poetry và làm theo dựa trên hệ điều hành của mình.

### 3.4. Kết hợp Poetry và Pyenv

```bash
# Tạo một dự án với Poetry
poetry new my-project

# Xem dự án được tạo ra
cd my-project
ls

# Cài đặt phiên bản Python
pyenv versions
pyenv install --list
pyenv install <version>

# Chỉ định phiên bản Python
pyenv local <version>
poetry env use python
```

```bash
# Cài đặt các package cho Project
poetry add <pack_name>
poetry install

# update các package
poetry update

# Xóa package
poetry remove package_to_remove
```

```bash
# Trường hợp thay đổi phiên bản Python
# Chúng ta phải chạy các câu lệnh dưới đây
pyenv install <new_version>
pyenv local <new_version>
poetry env use python
poetry install
```

```bash
# Activate environment
# After, run Project in VS Code
poetry shell
code .
```

---