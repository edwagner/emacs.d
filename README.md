# Emacs config

Based on https://github.com/purcell/emacs.d

## Installation

To install, clone this repo to `~/.emacs.d`, i.e. ensure that the
`init.el` contained in this repo ends up at `~/.emacs.d/init.el`:

```
git clone git@github.com:edwagner/emacs.d.git ~/.emacs.d
```

To make the most of the programming language-specific support in this
config, further programs will likely be required, particularly those
that [flycheck](https://github.com/flycheck/flycheck) uses to provide
on-the-fly syntax checking.

```
brew install hadolint # Dockerfile
brew install tidy-html5
brew install jq # JSON
gem install haml # Need to test this to make sure it invokes rvm
gem install rubocop
npm install -g csslint
npm i -g eslint # May need configuration file
npm install -g markdownlint-cli
npm install -g sass-lint
```

Upon starting up Emacs for the first time, further third-party
packages will be automatically downloaded and installed. If you
encounter any errors at that stage, try restarting Emacs, and possibly
running `M-x package-refresh-contents` before doing so.

### Installing Emacs on Mac

```
brew install --cask emacs
```

This also sets up emacsclient.

## Updates

### Upstream Remote

If you haven't already configured the upstream remote (`git remote -v`), do so
```
git remote add upstream https://github.com/purcell/emacs.d.git
```

### Fetch From Upstream

```
git fetch upstream
git co master
git rebase upstream/master
```

You'll probably also want/need to update the third-party packages regularly too:

<kbd>M-x package-list-packages</kbd>, then <kbd>U</kbd> followed by <kbd>x</kbd>.

You should usually restart Emacs after pulling changes or updating
packages so that they can take effect. Emacs should usually restore
your working buffers when you restart due to this configuration's use
of the `desktop` and `session` packages.

## Changing themes and adding your own customization

To add your own customization, use <kbd>M-x customize</kbd>, <kbd>M-x
customize-themes</kbd> etc. and/or create a file
`~/.emacs.d/lisp/init-local.el` which looks like this:

```el
... your code here ...

(provide 'init-local)
```

If you need initialisation code which executes earlier in the startup process,
you can also create an `~/.emacs.d/lisp/init-preload-local.el` file.

