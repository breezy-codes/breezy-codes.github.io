# to update the book - 

cd /home/breezy/Documents/GitHub/Jupyter-Books

jupyter-book build breezy-codes.github.io

or rebuild with

jupyter-book build --all breezy-codes.github.io

# to push the book to GitHub Pages -

cd /home/breezy/Documents/GitHub/Jupyter-Books/breezy-codes.github.io

make sure in main - 

ghp-import -n -p -f _build/html
