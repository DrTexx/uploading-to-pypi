# uploading-to-pypi

__NOTE__: ALL COMMANDS EXECUTED WHILE IN ROOT DIRECTORY

1. Update the value of 'version' in setup.py
   
    (no commands, only script editting)
    
    _example_: `version='0.1b3'`

2. Create a new git tag for the version (this should match the one in setup.py)

        $ git tag <version> -m "<version message/note>"

   example: `$ git tag 0.1b3 -m "improved documentation"`

3. Sync local tags to github

        $ git push --tags origin master

4. Create a wheel for current version

        $ python setup.py bdist_wheel

   [NOTE!] do not run this command while Dropbox sync is active on Windows, it will break stuff

5. Upload the wheel to testpypi

        $ twine upload --repository test dist/*

   [url]: https://test.pypi.org/legacy/

6. Upload the wheel to pypi

        $ twine upload --repository pypi dist/*

   [url]: https://upload.pypi.org/legacy/
