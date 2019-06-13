# Blender Manual Maker

Script to help rebuilding the Blender manual.
I use it as part of a pipeline inside VS Code.

## First Steps
* Download and build the Blender manual following the official instructions.
* I recommend the [Browser Preview](https://marketplace.visualstudio.com/items?itemName=auchenberg.vscode-browser-preview)
extension in Visual Studio Code to check your changes after you rebuild.

## Usage

```
$./blender-manual-maker DOCS_FOLDER [/full/path/to/file/that/changed.rst]
```


## Visual Studio Code

I like to open the `//manual` subfolder in VS Code, to limit the files I see.

So the example below uses `"${workspaceFolder}/../"` to pass the base folder where I checked the Blender docs.

*tasks.json example*:
```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Rebuild Current Document",
            "type": "shell",
            "command": "blender-manual-maker",
            "args": [
                "${workspaceFolder}/../",
                "${file}"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": []
        },
        {
            "label": "Rebuild All Documents",
            "type": "shell",
            "command": "blender-manual-maker",
            "args": [
                "${workspaceFolder}/../"
            ],
            "group": "build"
        }
    ]
}
```

### Workflow

* Edit to your heart's content.
* Build with `Ctrl + Shift + B`.
* Hit refresh in the *Browser Preview*.

![Visual Studio Code](http://www.dalaifelinto.com/ftp/vs-code-screenshot.png)

## Advanced Tips
* It is better to use [virtual environment](https://docs.python-guide.org/dev/virtualenvs/) to install the python tools to build the manual.
If you do so make sure to create it as `venv` under the blender_docs folder.
* If you are familiar with git I highly recommend [git-svn](https://git-scm.com/docs/git-svn) as a middle layer between your workflow and Blender manual svn repository.
