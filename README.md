# tianjiaoling.github.io
## Install Hexo

```bash
sudo apt-get install nodejs-legacy npm
sudo npm install -g hexo-cli
```

## Clone website

```bash
git clone https://github.com/tianjiaoling/tianjiaoling.github.io
cd tianjiaoling.github.io && git submodule init && git submodule update
```

## Install node_modules

```bash
cd  tianjiaoling.github.io&& npm install
```

## Preview on localhost

```bash
hexo s
```

## Generate and deploy

```bash
hexo d -g
