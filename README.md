# Description
Generic Python template for AWE Group

## :gear: Installation

### Dependencies

- Sphinx Dependencies, see [requirements](requirements.txt)

## Installation Instructions

1. Navigate to the repository folder, using the terminal with commands change-directory `cd` and path using the `tab` key will give suggestion for folders
    ```bash
    cd < enter path >
    ```
2. Clone the repository, use the `git clone,` and copy from HTTPS. For the template, this would be:
    ```bash
    git clone https://github.com/awegroup/template-python.git
    ```


4. Create a virtual environment:
   
   Linux or Mac:
    ```bash
    python3 -m venv venv
    ```
    
    Windows:
    ```bash
    python -m venv venv
    ```
    
5. Activate the virtual environment:

   Linux or Mac:
    ```bash
    source venv/bin/activate
    ```

    Windows
    ```bash
    .\venv\Scripts\activate
    ```

6. Install the required dependencies:

   For users: (using package manager [pip](https://pip.pypa.io/en/stable/))

    ```bash
    pip install .
    ```
        
   For developers:
    ```bash
    pip install -e .[dev]
    ```

7. To deactivate the virtual environment:
    ```bash
    deactivate
    ```

## :eyes: Usage

```python
import foobar

# returns 'words'
foobar.pluralize('word')

# returns 'geese'
foobar.pluralize('goose')

# returns 'phenomenon'
foobar.singularize('phenomena')
```
## :wave: Contributing (optional)

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## :warning: License and Waiver

Specify the license under which your software is distributed, and include the copyright notice:

> Technische Universiteit Delft hereby disclaims all copyright interest in the program “NAME PROGRAM” (one line description of the content or function) written by the Author(s).
> 
> Prof.dr. H.G.C. (Henri) Werij, Dean of Aerospace Engineering
> 
> Copyright (c) [YEAR] [NAME SURNAME].

## :gem: Help and Documentation
[AWE Group | Developer Guide](https://awegroup.github.io/developer-guide/)


