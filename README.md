# uploading-to-pypi

__NOTE__: ALL COMMANDS EXECUTED WHILE IN ROOT DIRECTORY

1. If you have unittests, run them first

   ![Example](Example-Tag-V3.svg) `$ pytest`

1. Update the value of 'version' in setup.py
    
    ![Example](Example-Tag-V3.svg) `version='0.1b3'`

1. Create a new git tag for the version and push (this should match the one in setup.py)

        $ git tag <version> -m "<version message/note>"
        $ git push --tags origin master

   ![Example](Example-Tag-V3.svg) `$ git tag 0.1b3 -m "improved documentation"`

1. Create a wheel for current version

        $ python setup.py bdist_wheel

   ![Warning](Warning-Tag-V3.svg) Do not run this command while Dropbox sync is active on Windows, it may break stuff!

1. Upload the wheel to testpypi

        $ twine upload --repository test dist/*

   [url]: https://test.pypi.org/legacy/

1. Upload the wheel to pypi

        $ twine upload --repository pypi dist/*

   [url]: https://upload.pypi.org/legacy/
