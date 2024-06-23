### prometheus helm install


## pre install (linuxbrew && helm)
```
sudo apt-get install build-essential curl file git
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
```
- add path into environment in linux
```
touch ~/.zshrc
vim ~/.zshrc

export PATH="/home/linuxbrew/.linuxbrew/bin:$PATH"
export MANPATH="/home/linuxbrew/.linuxbrew/share/man:$MANPATH"
export INFOPATH="/home/linuxbrew/.linuxbrew/share/info:$INFOPATH"

source ~/.zshrc
```
* 만약 해당 path를 항상 적용하고싶으면 bashrc에 적용

- helm install
```
brew install helm
```

## install

```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install [RELEASE_NAME] prometheus-community/kube-prometheus-stack
```




## reference
1) official page
https://github.com/prometheus-community/helm-charts/tree/main
2) reference
https://wanbaep.tistory.com/21



