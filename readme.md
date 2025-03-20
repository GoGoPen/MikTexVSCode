# Tutorial for Miktex in VSCode

- Install MikTex https://miktex.org/download
- Install the TexLive base
```sudo apt-get install texlive-latex-base```

- Also install the recommended and extra fonts to avoid running into the error [1], when trying to use pdflatex on latex files with more fonts.
  
```
sudo apt-get install texlive-fonts-recommended
sudo apt-get install texlive-fonts-extra
```

- Install the extra packages,
```sudo apt-get install texlive-latex-extra```

You may also need to add your executable to PATH
echo export 'PATH=<your executable path>:$PATH' >> ~/.bash_profile

- Install LaTeX Workshop in VSCode
- Edit Plugin settings.json

```
{
    "latex-workshop.latex.recipes": [
        {
            "name": "pdflatex",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "pdflatex -> bibtex -> pdflatex*2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        }
    ],
    "latex-workshop.latex.tools": [
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],

    "latex-workshop.viewer.pdf.viewer": "tab",
    "latex-workshop.latex.autoBuild.interval": 30000,
    "latex-workshop.latex.autoClean.run": "onBuilt",
    "latex-workshop.latex.recipe.default": "lastUsed"}
```

- Create your tex file to test.