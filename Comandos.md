
# Criando tabelas

```sql
CREATE TABLE table (column type, ...);
```
-  _table_ sendo o nome da tabela a ser desejada
-  _column_ sendo o nome da coluna seguido de seu tipo (_type_)

OBS: **SEMPRE** que for utilizar a sintaxe do SQL, colocar em **LETRAS MAISCULAS** para justamente diferenciar do que é nomeado pelo desenvolvedor dos comandos do SQL em si, visto que sua sintaxe usa de palavras humanas, por assim dizer.

---

# Inicializando

```
sqlite3 favorites.db
```

O recomendado é sempre estar inicializando o sqlite3 juntamente com a database que quiser utilizar. Caso ela não exista, o sqlite automaticamente cria pra você.
Nesse exemplo, o sqlite abriria a database _favorites.db_ se existisse, e caso não, criaria uma nova com esse nome.
```sql
.mode
.import
.schema
```
OBS: Esses comandos são **exclusivos** do SQLite, que uma versão mais leve do SQL original, por assim dizer.
1. O comando _.mode_ alterna o modo de visualização/edição do SQL, que por padrão deixa como o próprio SQL mas existem outros modos. No CS50x é apresentado somente o _csv_.
2. _.import_ justamente importa um arquivo existente seja na pasta raiz no qual o SQLite foi executado ou através do caminho dado até esse arquivo.
```sql
.import favorites.csv favorites
```
Nesse exemplo, importamos o arquivo _favorites.csv_ e com os dados contidos nele criamos uma tabela com o nome de _favorites_.
3. _.schema_ mostra o código que a database.
```sql
.schema
-> CREATE TABLE IF NOT EXISTS "favorites"("Timestamp" TEXT, "language" TEXT, "problem", TEXT);
```

---
# Acessando dados

```sql
SELECT columns FROM table;
```
- Caso queira acessar mais de uma coluna da mesma tabela, é só separar por vírgula.
	- Agora caso queira selecionar todas as colunas de uma tabela, é só utilizar o wildcard _*_

---
# Inserindo dados

```sql
INSERT INTO table (column, ...) VALUES (value, ...);
```
- Caso for adicionar mais de uma coluna, os valores a serem inseridos devem ser na mesma ordem que as colunas foram selecionadas.

---
# Alterando/Atualizando dados

```sql
UPDATE table SET column = value WHERE condition;
```
- Nesse exemplo, a alteração somente será realizada na coluna de acordo com a condição _WHERE_ for cumprida.

```sql
UPDATE favorites SET language = 'C++' WHERE language = 'C';
```
- Aqui, todos os valores da coluna _language_ que são "C" irão ser alterados para "C++".

***Esse comando pode alterar drasticamente uma tabela e não tá nem aí pra nada. Sempre utilize um predicado (condição) e/ou tenha um backup de sua database em qualquer alteração.***



---

# Funções
Assim como em outras linguagens, no SQL também encontramos funções prontos que a linguagem nos oferece e que podem ser utilizadas em cada query.

### COUNT (_columns_)
```sql
SELECT COUNT(*) FROM favorites;
```
Auto-explicativo, conta todos os elementos contidos na coluna desejada.
### DISTINCT()
```sql
SELECT DISTINCT(languages) FROM favorites;
```
Devolve todos os valores, porém ignora todas as suas repetições caso houver.

