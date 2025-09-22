# Sistema de RH 👥

Aplicativo acadêmico em **Java** para gestão básica de **Recursos Humanos**: cadastro de colaboradores, cargos/setores, controle de ponto/folhas e geração de relatórios simples, com **importação/exportação em CSV** e interface (Swing). Foco em **POO**, camadas e manipulação de arquivos.

## 🎯 Objetivos
- Gerenciar **colaboradores**, **cargos** e **setores**
- Registrar **jornada/ponto** e **lançamentos de folha** (proventos/descontos)
- Importar/exportar dados em **CSV**
- Exercitar boas práticas de arquitetura e POO

## 🧰 Stack
- Java 17+ (compatível com 11)
- Swing (GUI)
- Ant / Maven / Gradle (qualquer um — ver seção de build)
- Manipulação de arquivos CSV

## ✨ Funcionalidades
- CRUD de colaboradores, cargos e setores
- Controle de ponto (entrada/saída) e cálculo básico de horas
- Lançamentos simples de folha (salário base, adicional, desconto)
- Importação/exportação CSV
- Validações básicas e interface amigável

## 🗂️ Estrutura (sugerida após extrair o zip)
```
/src/...
/data/                 # dados CSV (git-ignored, usar *.example)
docs/                  # capturas de tela, diagramas
/dist/                 # artefatos de build (git-ignored)
```

## ▶️ Como executar

### Opção A) Via NetBeans
1. **Extraia** o conteúdo do `.zip` para a raiz do repositório (ou abra o projeto extraído).
2. Abra no NetBeans e execute o projeto.

### Opção B) Via linha de comando
- **Se houver `build.xml` (Ant):**
  ```bash
  ant clean dist
  ```
- **Se houver `pom.xml` (Maven):**
  ```bash
  mvn -B -DskipTests package
  ```
- **Se houver `build.gradle`:**
  ```bash
  ./gradlew build
  ```
- **Sem ferramenta de build (apenas fontes em `/src`):**
  ```bash
  find src -name "*.java" > sources.txt
  javac -d out @sources.txt
  java -cp out Main
  ```

> **CI**: O GitHub Actions detecta automaticamente Ant/Maven/Gradle. Se só houver `.java`, ele compila “na unha”. Se existir um `.zip` com o projeto, o CI **descompacta antes** de compilar.

## 📄 CSV (padrões sugeridos)

### `data/colaboradores.csv`
```
colaborador_id,nome,documento,cargo_id,setor_id,admissao,salario_base,email,telefone
```

### `data/cargos.csv`
```
cargo_id,nome,salario_referencia,carga_horaria_semanal
```

### `data/setores.csv`
```
setor_id,nome,descricao
```

### `data/ponto.csv`
```
ponto_id,colaborador_id,data,hora_entrada,hora_saida,horas_trabalhadas,observacao
```

### `data/folha.csv`
```
folha_id,colaborador_id,competencia,proventos,descontos,liquido,observacao
```

- Codificação: UTF-8
- Separador: `,`
- Exemplos em `data/*.csv.example`

## 🛣️ Roadmap
- [ ] Serviços e repositórios separados por domínio
- [ ] Cálculo mais detalhado de folha (FGTS/INSS/IRPF simulados)
- [ ] Relatórios (PDF/Excel)
- [ ] Perfis de acesso (admin/operacional)
- [ ] Persistência opcional com SQLite

## 🤝 Contribuição
Sinta-se à vontade para abrir issues e PRs! Padrões:
- Conventional Commits
- Branches: `feature/*`, `fix/*`
- PR com descrição clara e prints quando relevante

## 📜 Licença
Este projeto é licenciado sob **MIT**. Veja [LICENSE](LICENSE).
