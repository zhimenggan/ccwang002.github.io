---
Title: Learning Python
Slug: learn-python
Date: 2017-11-07
Tags: en, python
Category: Coding
Status: draft
---

Here I collect some useful resources to learn Python and its common use cases in various specific topics. Please take my personal recommendations with a grain of salt and I don't have any opinion to ask people to use Python in a certain way. If you are fine with the current way you use Python, keep it. Various resources will be books from O'Reilly publisher, which are free to view on the Safari platform via WUSTL network.

## Beginning Python

### Should I learn Python 2 or 3?
Learn Python 3. Python 2.7 is a legacy and will [reach its end of life by 2020﻿][python2.7-eol]. They are very similar and it is easier to learn Python 2.7 after learning the latest Python 3 version.

[python2.7-eol]: https://pythonclock.org/

### Starting material
[The official Python tutorial][official-tutorial] is a concise introduction which covers most aspects of the language. It would be helpful to understand how Python developers introduce their language since the rest of the documentations like Python's standard libaray and many 3rd party packages are written in the similar style and tone. It is also important to know how to navigate the documentation since nearly all the Python documentations are generated by the same tool.

A longer and detailed version of Python introduction is the book [*Introducing Python* by Bill Lubanovic, O'Reilly (2014)][introducing-python]. The book includes more application examples and covers some commonly used 3rd party packages. Although it is longer, usually you will be able to work on your own script about half way through the book. People generally finish the rest of the chapters when they feel like it.

I don't recommend the following materials:

- Learn Python the Hard Way (Received bad reputation generally and serious criticism from core developers)
- Learning Python (Too detailed for beginners)

[official-tutorial]: https://docs.python.org/3/tutorial/index.html
[introducing-python]: http://shop.oreilly.com/product/0636920028659.do

### How to search the documentations
Python is a ["batteries included"][python-xkcd] language, meaning it has a feature-rich [standard library] which comes with the Python installation. A lot of daily usage can be handled the functions provided by the standard library without any dependencies. However the problem is that it is hard to find which module to import and few people has the time to read all the built-in modules (Spoiler: there are more than 150 modules in the standard library).

The documentation comes with a very simple text search box and turns out it actually works. Say you want to search a module that has the class `Counter`, [here](https://docs.python.org/3/search.html?q=Counter&check_keywords=yes&area=default) is the output from the search. The search machinery comes by default so it should be also available in the 3rd party packages' documentation. However, it is a full text search so expect high false positives.

If you already know the function you want to use, another way to search its documentation is via <https://devdocs.io/>. If you try the same example, it will lead you directly to [the correct entry](https://devdocs.io/python~3.6/library/collections#collections.Counter). devdocs.io also includes documentations from some famous 3rd party packages like numpy and pandas. On macOS, a paid app [Dash] does a better job with a nicer user interface and includes much more documentations.

[python-xkcd]: https://xkcd.com/353/
[standard library]: https://docs.python.org/3/library/index.html
[Dash]: https://kapeli.com/dash



## Using Python Standard Library
There are many hidden gems in the standard library and can save many developers' time if they knew such modules exist.


### Books
Some books cover the standard library in a systematic manner. Notably the following two books:

- [*Fluent Python* by Luciano Ramalho, O'Reilly (2015)](http://shop.oreilly.com/product/0636920032519.do)
- [*Python Cookbook* 3rd edition by Brian Jones and David Beazley, O'Reilly (2013)](http://shop.oreilly.com/product/0636920027072.do)


### `pathlib`: managing system path


### `collections`: useful data structure

- `collections.Counter`
- `collections.namedtuple`
- `collections.defaultdict`


### `logging`: unified log messaging
The documentations are a bit complicated so I include an example here

```py
import loggging
logger = logging.getLogger(__name__)

def main():
    ans = 41
    logger.warning(f'ans should be 42 instead of {ans}')


if __name__ == '__main__':
    # Setup console logging
    console = logging.StreamHandler()
    all_loggers = logging.getLogger()
    all_loggers.setLevel(logging.INFO)
    all_loggers.addHandler(console)
    log_fmt = '[%(asctime)s][%(levelname)-7s][%(name)-8s] %(message)s'
    log_formatter = logging.Formatter(log_fmt, '%Y-%m-%d %H:%M:%S')
    console.setFormatter(log_formatter)

    main()
```


### `argparse`: building command-line application



## Other intermediate Topics


### How to find the suitable / most widely used 3rd party packages?
Try browse [Awesome Python] and evaluate the packages listed at the same category. Usually I will go to their GitHub/Bitbucket/GitLab page to see it is still actively maintained (commit history, stars, activity on replying issues and so on).

[Awesome Python]: https://awesome-python.com/


### How to write 2.7 and 3.x compatible code in a single codebase?
Use [python-future] or [six].


### `py.test`: testing

[python-future]: http://python-future.org/
[six]: https://pythonhosted.org/six/