# GitHub_as_package
How to make GitHub repository to be installed as a Python package

## Repository to be installed

### How to make repository
1. Creates `setup.py` in the root of the repository
2. Fills in informations in `setup.py`
    ```
    import os

    import pkg_resources
    from setuptools import setup, find_packages

    setup(
        name="SofaGW",
        py_modules=["SofaGW"],
        version="1.0.8",
        description="Use SOFA framework for guidewire navigation.",
        url="https://github.com/candi4/SofaGuidewireNav.git",
        author="candi4",
        packages=find_packages(),
        install_requires=[
            str(r)
            for r in pkg_resources.parse_requirements(
                open(os.path.join(os.path.dirname(__file__), "requirements.txt"))
            )
        ],
        include_package_data=False,
        package_data={
            'SofaGW': ['vessel/*'],
        },
    )
    ```
    * `name` : Should be same as the folder name of package (not sure)
    * `py_modules` : Should be same as the folder name of package (not sure)
    * `version` : To be seen in pip
    * `description` : To be seen in pip
    * `url` : To be seen in pip
    * `author` : To be seen in pip
    * `packages` : Files to be included or excluded in the repository
    * `install_requires` : Other packages to be installed automatically
    * `include_package_data` : If true, installation includes non-code files in the repository (doesn't work)
    * `package_data` : Non-code files to be included by installation.    
    The key is module name and the elements of the list are non-code files wanted to install

### How to install repository
1. From default branch
    ```
    pip install git+https://github.com/candi4/SofaGuidewireNav.git
    ```
2. From specific branch
    ```
    pip install git+https://github.com/candi4/SofaGuidewireNav.git@branchname
    ```
3. In `requirements.txt`
    ```
    SofaGW @ git+https://github.com/candi4/SofaGuidewireNav.git
    ```
### References
* [github repository로 python pip install 만드는 방법 정리](https://lsjsj92.tistory.com/592)
* [Python 프로젝트를 패키지로 만들기 with setup.py](https://velog.io/@rhee519/python-project-packaging-setuptools)
* [Adding Non-Code Files](https://python-packaging.readthedocs.io/en/latest/non-code-files.html)
* [Python » 설명서 » 파이썬 모듈 배포 (레거시 버전) » 2.6. 패키지 데이터 설치하기](https://python.flowdas.com/distutils/setupscript.html#installing-package-data)
* [GitHub repository CLIP/setup.py](https://github.com/openai/CLIP/blob/main/setup.py)


## TODO
* `git submodule update --recursive --init`