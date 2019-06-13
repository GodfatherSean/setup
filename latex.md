# Setting up LaTeX on a Mac with VS Code

## MacTex Installation

First download the latest distribution of the MacTeX package.

```bash
curl http://tug.org/cgi-bin/mactex-download/MacTeX.pkg > ~/Downloads/MacTex.pkg
```

Then install the package using command line.

```bash
sudo installer -pkg ~/Downloads/MacTeX.pkg -target /
```

## VS Code Extension

After installation open VS Code.

```bash
open -a Code
```

Pull up quick open in VS Code by `Command+P` and then install the extension LaTeX Workshop.

```bash
ext install latex-workshop
```

Now you can write LaTex documents with real time rendering.
