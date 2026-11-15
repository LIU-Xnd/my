# How to Globalize Conda-Installed Apps

`conda install zoxide` will install zoxide into `~/miniforge3/bin/`.
First, you want to `mkdir -p ~/.local/bin/`, and then
`echo 'export PATH="$PATH:~/.local/bin"' >> ~/.bashrc`. Then
`ln -s ~/miniforge3/bin/zoxide ~/.local/bin/zoxide`, along with its
dependency: `ln -s ~/miniforge3/bin/fzf ~/.local/bin/fzf`.

2026-11-15 21:55

