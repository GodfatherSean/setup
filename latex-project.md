# Setting up LaTeX Project with Git

## LaTeX Tool Installation

Please refer to [latex.md](latex.md) for more details.

## Ignore list

Paste the following content to .gitignore.

```gitignore
.vscode
.idea
*.pdf
*.aux
*.fdb_latexmk
*.fls
*.log
*.out
*.synctex.gz
```

## Project Structure

Make sure you put each latex file into a folder under the project root and make sure that each folder only contains one latex file. After this step, each latex file will have the same filename. In my case, the common name is solution.tex. For now the batch compilation script only works for this setup. Below is an example.

```structure
.
+-- .gitignore
+-- .compile.sh
+-- hw01/
|   +-- solution.tex
+-- hw02/
|   +-- solution.tex
+-- hw03/
|   +-- solution.tex
```

## Batch compilation script

Paste the following content to compile.sh.

```bash
function compile () {
    echo "compiling $1 .........";
    cd $1;
    pdflatex solution.tex;
    rm -f *.aux;
    rm -f *.fdb_latexmk;
    rm -f *.fls;
    rm -f *.log;
    rm -f *.out
    cd ..;
    echo "compiling $1 finished!";
    echo "";
}

if [ "$1" = all ]; then
    for d in `ls -d hw*/`; do
        compile $d &
    done
else
    compile hw$1
fi
```

Then in project root, type `chmod +x compile.sh` to give the script execution privileges. Then you can type `./compile.sh all` to automatically compile all latex source files. You can type `./compile.sh dir` to compile the latex source file under directory `dir`.
