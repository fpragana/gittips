# GitTips
## Comandos GIT para melhoras a produtividade
### Localizar em quais commits determinada linha de um arquivo foi modificada
```
git log -L123,123:caminho/relativo/do/arquivo/arquivo.ext
```
### Listar Branchs abertos em que seu usuário foi o último a dar commit
```
git ls-remote -h origin | while read b; do PAGER='' git log -n1 --color --pretty=format:'%ct%C(yellow)%d%Creset - %Cred%h%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset%n' --abbrev-commit $( echo $b | cut -d' ' -f1 ) --; done | sort -rn -k1,10 | cut -c11- | grep "<$(git config user.name)>"
```
### Listar commits aonde houve alteração de uma parte especifica de código (2 formas)
```
git log -G "PARTE DO FONTE ALTERADO A SER LOCALIZADO" caminho/relativo/do/arquivo/arquivo.ext
```
```
for c in $(git log -G "PROCEDURE PROCESSA_SOLICITACAO_ELETRONIC" --format=%H -- Medico/src/oracle/packages/TS_MASTER.TSS_INTEGRACAO_V030500_DDL.SQL); do
    git --no-pager grep -e "PROCEDURE PROCESSA_SOLICITACAO_ELETRONIC" $c -- Medico/src/oracle/packages/TS_MASTER.TSS_INTEGRACAO_V030500_DDL.SQL
done
```
