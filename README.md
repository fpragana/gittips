# GitTips
## Comandos GIT para melhoras a produtividade
### Localizar em quais commits determinada linha de um arquivo foi modificada
```
git log -L123,123:caminho/relatio/do/arquivo/arquivo.ext
```
### Listar Branchs abertos em que seu usuário foi o último a dar commit
```
git ls-remote -h origin | while read b; do PAGER='' git log -n1 --color --pretty=format:'%ct%C(yellow)%d%Creset - %Cred%h%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset%n' --abbrev-commit $( echo $b | cut -d' ' -f1 ) --; done | sort -rn -k1,10 | cut -c11- | grep "<$(git config user.name)>"
```

