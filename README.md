#Canonical Correlation Forest Classifier 

[![Travis Status](https://travis-ci.org/fmaguire/Canonical-Correlation-Forest.svg?branch=master)](https://travis-ci.org/fmaguire/Canonical-Correlation-Forest)

[![Coveralls Status](https://coveralls.io/repos/fmaguire/Canonical-Correlation-Forest/badge.svg?branch=master&service=github)](https://coveralls.io/r/fmaguire/Canonical-Correlation-Forest)
[![CircleCI Status](https://circleci.com/gh/fmaguire/Canonical-Correlation-Forest.svg?style=shield&circle-token=:circle-token)](https://circleci.com/gh/fmaguire/Canonical-Correlation-Forest/tree/master)

Implementation of Rainforth and Wood's 
[Canonical Correlation Forest](http://arxiv.org/abs/1507.05444) 
classifier in a [scikit-learn](http://scikit-learn.org)
compatible [scikit-learn-contrib](https://github.com/scikit-learn-contrib/scikit-learn-contrib) project.

## Important Links
HTML Documentation - 

## Installation and Usage
The package by itself comes with a single module and a classifier. Before
installing the module you will need `numpy`, and `scipy`.
To install the module execute:
```shell
$ python setup.py install
```
or 
```
pip install Canonical-Correlation-Forest
```

If the installation is successful, and `scikit-learn` is correctly installed,
you should be able to execute the following in Python:
```python
>>> from Canonical-Correlation-Forest import CCF
>>> classifier = CCF()
>>> classifier.fit(np.arange(20).reshape(10, 2), np.vstack(np.full(5, 0), np.full(5, 1)))
```

`TemplateEstimator` by itself does nothing useful, but it serves as an example
of how other Estimators should be written. It also comes with its own unit
tests under `template/tests` which can be run using `nosetests`.


### 2. Modifying the Source
You are free to modify the source as you want, but at the very least, all your
estimators should pass the [`check_estimator`](http://scikit-learn.org/stable/modules/generated/sklearn.utils.estimator_checks.check_estimator.html#sklearn.utils.estimator_checks.check_estimator)
test to be scikit-learn compatible.
(If there are valid reasons your estimator cannot pass `check_estimator`, please
[raise an issue](https://github.com/scikit-learn/scikit-learn/issues/new) at
scikit-learn so we can make `check_estimator` more flexible.)


In any case, developers should endeavor to adhere to scikit-learn's
[Contributor's Guide](http://scikit-learn.org/stable/developers/) which promotes
the use of:
* algorithm-specific unit tests, in addition to `check_estimator`'s common tests
* [PEP8](https://www.python.org/dev/peps/pep-0008/)-compliant code
* a clearly documented API using [NumpyDoc](https://github.com/numpy/numpydoc)
  and [PEP257](https://www.python.org/dev/peps/pep-0257/)-compliant docstrings
* references to relevant scientific literature in standard citation formats
* [doctests](https://docs.python.org/3/library/doctest.html) to provide
  succinct usage examples
* standalone examples to illustrate the usage, model visualisation, and
  benefits/benchmarks of particular algorithms
* efficient code when the need for optimization is supported by benchmarks

### 3. Modifying the Documentation

The documentation is built using [sphinx](http://www.sphinx-doc.org/en/stable/).
It incorporates narrative documentation from the `doc/` directory, standalone
examples from the `examples/` directory, and API reference compiled from
estimator docstrings.

To build the documentation locally, ensure that you have `sphinx`,
`sphinx-gallery` and `matplotlib` by executing:
```shell
$ pip install sphinx matplotlib sphinx-gallery
```
The documentation contains a home page (`doc/index.rst`), an API
documentation page (`doc/api.rst`) and a page documenting the `template` module 
(`doc/template.rst`). Sphinx allows you to automatically document your modules
and classes by using the `autodoc` directive (see `template.rst`). To change the
asthetics of the docs and other paramteres, edit the `doc/conf.py` file. For
more information visit the [Sphinx Documentation](http://www.sphinx-doc.org/en/stable/contents.html).

You can also add code examples in the `examples` folder. All files inside
the folder of the form `plot_*.py` will be executed and their generated
plots will be available for viewing in the `/auto_examples` URL.

To build the documentation locally execute
```shell
$ cd doc
$ make html
```
### 8. Advertising your package

Once your work is mature enough for the general public to use it, you should
submit a Pull Request to modify scikit-learn's
[related projects listing](https://github.com/scikit-learn/scikit-learn/edit/master/doc/related_projects.rst).
Please insert brief description of your project and a link to its code
repository or PyPI page.
You may also wish to announce your work on the
[`scikit-learn-general` mailing list](https://lists.sourceforge.net/lists/listinfo/scikit-learn-general).

### 9. Uploading your package to PyPI

Uploading your package to [PyPI](https://pypi.python.org/pypi) allows users to
install your package through `pip`. Python provides two repositories to upload
your packages. The [PyPI Test](https://testpypi.python.org/pypi) repository,
which is to be used for testing packages before their release, and the
[PyPI](https://pypi.python.org/pypi) repository, where you can make your
releases. You need to register a username and password with both these sites.
The username and passwords for both these sites need not be the same. To upload
your package through the command line, you need to store your username and
password in a file called `.pypirc` in your `$HOME` directory with the
following format.

```shell
[distutils]
index-servers =
  pypi
  pypitest

[pypi]
repository=https://pypi.python.org/pypi
username=<your-pypi-username>
password=<your-pypi-passowrd>

[pypitest]
repository=https://testpypi.python.org/pypi
username=<your-pypitest-username>
password=<your-pypitest-passowrd>
```
Make sure that all details in `setup.py` are up to date. To upload your package
to the Test server, execute:
```
python setup.py register -r pypitest
python setup.py sdist upload -r pypitest
```
Your package should now be visible on: https://testpypi.python.org/pypi

To install a package from the test server, execute:
```
pip install -i https://testpypi.python.org/pypi <package-name>
```

Similary, to upload your package to the PyPI server execute
```
python setup.py register -r pypi
python setup.py sdist upload -r pypi
```
To install your package, execute:
```
pip install <package-name>
```

*Thank you for cleanly contributing to the scikit-learn ecosystem!*
