# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Scripting installer](#scripting-installer)

## Scripting installer

It uses controller scripting described in [Link](https://doc.qt.io/qtinstallerframework/noninteractive.html) Called with script and invalid proxy to prevent network access:

```bash
export https_proxy=1.2.3.4; sudo --preserve-env=https_proxy ./qt-opensource-linux-x64-5.12.8.run --script install_qt.qs
```

To get elements in widget call with logging in verbose mode like:

```bash
Controller.prototype.WelcomePageCallback = function() {
    var widget = gui.currentPageWidget();
    console.log(JSON.stringify(widget));
}
```

Some useful info at [Link](https://stackoverflow.com/questions/25105269/silent-install-qt-run-installer-on-ubuntu-server)
