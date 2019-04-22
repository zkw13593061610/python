## python的一些操作

### 上传包

- 首先安装工具    python -m pip install setuptools wheel twine

- 创建以下目录 

  ```py
  /example_pkg
    /example_pkg
      __init__.py
  ```

- 您还应该编辑`example_pkg/__init__.py`并在其中放入以下代码： 

  ```py
  name = "example_pkg"   包名
  ```

- 创建包文件

  ```py
  /example_pkg
    /example_pkg
      __init__.py
    setup.py
    LICENSE
    README.md
  ```

- 创建的setup.py

  ```py
  import setuptools
  
  with open("README.md", "r") as fh:
      long_description = fh.read()
  
  setuptools.setup(
      name="example_pkg",
      version="0.0.1",
      author="Example Author",
      author_email="author@example.com",
      description="A small example package",
      long_description=long_description,
      long_description_content_type="text/markdown",
      url="https://github.com/pypa/sampleproject",
      packages=setuptools.find_packages(),
      classifiers=[
          "Programming Language :: Python :: 3",
          "License :: OSI Approved :: MIT License",
          "Operating System :: OS Independent",
      ],
  )
  
  name是您的包的名称。只要包含字母，数字_和，就可以是任何名称-。它也不能在pypi.org上使用。
  version 是包版本看 PEP 440有关版本的更多详细信息。
  author并author_email用于识别包的作者。
  description 是一个简短的，一句话的包的总结。
  long_description是包的详细说明。这显示在Python Package Index的包详细信息包中。在这种情况下，加载长描述README.md是一种常见模式。
  long_description_content_type告诉索引什么类型的标记用于长描述。在这种情况下，它是Markdown。
  url是项目主页的URL。对于许多项目，这只是一个指向GitHub，GitLab，Bitbucket或类似代码托管服务的链接。
  packages是应包含在分发包中的所有Python 导入包的列表。我们可以使用 自动发现所有包和子包，而不是手动列出每个包。在这种情况下，包列表将是example_pkg，因为它是唯一存在的包。find_packages()
  classifiers告诉索引并点一些关于你的包的其他元数据。在这种情况下，该软件包仅与Python 3兼容，根据MIT许可证进行许可，并且与操作系统无关。您应始终至少包含您的软件包所使用的Python版本，软件包可用的许可证以及您的软件包将使用的操作系统。有关分类器的完整列表，请参阅 https://pypi.org/classifiers/。
  ```

- 创建README.md

  ```py
  # Example Package
  
  This is a simple example package. You can use
  [Github-flavored Markdown](https://guides.github.com/features/mastering-markdown/)
  to write your content.
  ```

- 创建许可证

  ```py
  Copyright (c) 2018 The Python Packaging Authority
  
  Permission is hereby granted, free of charge, to any person obtaining a copy
  of this software and associated documentation files (the "Software"), to deal
  in the Software without restriction, including without limitation the rights
  to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
  copies of the Software, and to permit persons to whom the Software is
  furnished to do so, subject to the following conditions:
  
  The above copyright notice and this permission notice shall be included in all
  copies or substantial portions of the Software.
  
  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
  IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
  FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
  AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
  LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
  OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
  SOFTWARE.
  ```

- 生成分发档案

  ```py
  确保您拥有setuptools并wheel 安装了最新版本：
  python3 -m pip install --user --upgrade setuptools wheel
  现在从setup.py位于的同一目录运行此命令：
  python3 setup.py sdist bdist_wheel
  此命令应输出大量文本，一旦完成，应在dist目录中生成两个文件
  dist/
    example_pkg-0.0.1-py3-none-any.whl
    example_pkg-0.0.1.tar.gz
  ```

- 上传文档

  ```py
  twine upload dist/* 
  会看到下面的东西
  Uploading distributions to https://test.pypi.org/legacy/
  Enter your username: [your username]
  Enter your password:
  Uploading example_pkg-0.0.1-py3-none-any.whl
  100%|█████████████████████| 4.65k/4.65k [00:01<00:00, 2.88kB/s]
  Uploading example_pkg-0.0.1.tar.gz
  100%|█████████████████████| 4.25k/4.25k [00:01<00:00, 3.05kB/s]
  ```

### 创建虚拟环境：

- python3 -m venv tutorial-env(虚拟环境文件名称)
- cd tutorial-env
- source bin/activate （运行虚拟环境）就是进入到虚拟环境