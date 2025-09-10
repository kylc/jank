# Installing jank
If you're on any of the below systems, you can install jank using your system's
package manager.

## Homebrew (macOS or Linux)
### Install
There is no binary package for Homebrew yet, but there's a source package which
builds from git.

```sh
brew install jank-lang/jank/jank
```

If you get an error about `git-lfs`, try the following:

```sh
git lfs install
sudo ln -s "$(which git-lfs)" "$(git --exec-path)/git-lfs"
```

### Update
```bash
brew update
brew reinstall jank-lang/jank/jank
```

## Ubuntu Linux (24.04, 24.10)
### Install
We have binary jank packages in our PPA, so installation is quick and easy.

```bash
sudo apt install -y curl gnupg
curl -s "https://jank-lang.github.io/ppa/KEY.gpg" | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/jank.gpg >/dev/null
sudo curl -s -o /etc/apt/sources.list.d/jank.list "https://jank-lang.github.io/ppa/jank.list"
sudo apt update
sudo apt install -y jank
```

### Update
```bash
sudo apt update
sudo apt reinstall jank
```

## Arch Linux (AUR)
### Install
There is no binary AUR package yet, but there's a source package which builds from
git.

```bash
yay -S jank-git
```

### Update
```bash
yay -Syy
yay -S jank-git
```

## Nix
### Install
We have binary packages in our cachix cache, so installation is quick and easy.
You may also skip the cache setup and artifacts will be built from source.

```bash
# Make sure cachix is installed, then follow the prompts.
cachix use jank-lang
```

Next, you can directly run the jank binary from the nix flake derivation.

```bash
nix run git+https://github.com/jank-lang/jank.git?submodules=1 -- check-health
```

If you pull down the jank repository locally for development, you can enter the
dev shell and then follow the build instructions linked below. Skip the LLVM
build step as it's done for you by nix.

```bash
git clone https://github.com/jank-lang/jank.git
cd jank
nix develop
```

## Anything else
If nothing above matches what you have, you can still build jank by following
the docs [here](./build.md).
