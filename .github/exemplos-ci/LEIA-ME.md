# Como ativar o CI

O CI precisa executar **testes e lint** e falhar quando um deles falhar. Escolham **Node.js ou Java**, as linguagens permitidas no projeto, sigam a seção escolhida e confirmem o resultado na aba **Actions** do GitHub. Depois, façam um teste de propósito errado em uma branch: o CI precisa ficar vermelho.

As regras de lint abaixo são só um ponto de partida. Limites como complexidade e tamanho de função são decisão do grupo e devem constar nos RNFs.

## Node.js
Requer Node.js 22 ou superior.

1. Copiem o workflow:
   ```bash
   mkdir -p .github/workflows
   cp .github/exemplos-ci/ci-node.yml .github/workflows/ci.yml
   ```
2. Criem o `package.json`:
   ```json
   {
     "name": "meu-projeto",
     "version": "0.1.0",
     "private": true,
     "type": "module",
     "scripts": {
       "lint": "eslint .",
       "test": "node --test --test-reporter=spec --test-timeout=30000 \"test/**/*.test.js\""
     }
   }
   ```
3. Instalem o ESLint:
   ```bash
   npm install --save-dev eslint @eslint/js globals
   ```
4. Criem o `eslint.config.js`:
   ```js
   import js from '@eslint/js';
   import globals from 'globals';

   export default [
     js.configs.recommended,
     {
       files: ['**/*.js'],
       languageOptions: { globals: globals.node },
       rules: {
         // Regras e limites são decisão do grupo (RNF).
       },
     },
   ];
   ```
5. Coloquem os testes em `test/`, com nomes terminados em `.test.js`, e confiram:
   ```bash
   npm run lint
   npm test
   ```
6. Façam commit do `package.json` **e** do `package-lock.json`: o CI usa `npm ci`, que precisa dos dois.

## Java
Requer Java 17 e Maven.

1. Copiem o workflow:
   ```bash
   mkdir -p .github/workflows
   cp .github/exemplos-ci/ci-java.yml .github/workflows/ci.yml
   ```
2. Criem o `pom.xml`:
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <project xmlns="http://maven.apache.org/POM/4.0.0"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
     <modelVersion>4.0.0</modelVersion>
     <groupId>br.uepg</groupId>
     <artifactId>meu-projeto</artifactId>
     <version>0.1.0</version>
     <properties>
       <maven.compiler.release>17</maven.compiler.release>
       <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
     </properties>
     <dependencies>
       <dependency>
         <groupId>org.junit.jupiter</groupId>
         <artifactId>junit-jupiter</artifactId>
         <version>5.11.4</version>
         <scope>test</scope>
       </dependency>
     </dependencies>
     <build>
       <plugins>
         <plugin>
           <groupId>org.apache.maven.plugins</groupId>
           <artifactId>maven-compiler-plugin</artifactId>
           <version>3.13.0</version>
         </plugin>
         <plugin>
           <groupId>org.apache.maven.plugins</groupId>
           <artifactId>maven-surefire-plugin</artifactId>
           <version>3.5.2</version>
         </plugin>
         <plugin>
           <groupId>org.apache.maven.plugins</groupId>
           <artifactId>maven-checkstyle-plugin</artifactId>
           <version>3.6.0</version>
           <configuration>
             <configLocation>checkstyle.xml</configLocation>
             <consoleOutput>true</consoleOutput>
             <violationSeverity>warning</violationSeverity>
             <failOnViolation>true</failOnViolation>
           </configuration>
           <executions>
             <execution>
               <phase>verify</phase>
               <goals>
                 <goal>check</goal>
               </goals>
             </execution>
           </executions>
         </plugin>
       </plugins>
     </build>
   </project>
   ```
3. Criem o `checkstyle.xml` na raiz do projeto:
   ```xml
   <?xml version="1.0"?>
   <!DOCTYPE module PUBLIC "-//Checkstyle//DTD Checkstyle Configuration 1.3//EN"
     "https://checkstyle.org/dtds/configuration_1_3.dtd">
   <module name="Checker">
     <module name="TreeWalker">
       <module name="UnusedImports"/>
       <module name="AvoidStarImport"/>
       <module name="NeedBraces"/>
       <module name="EmptyCatchBlock"/>
       <module name="EqualsHashCode"/>
       <!-- Limites são decisão do grupo (RNF). -->
     </module>
   </module>
   ```
4. Coloquem o código em `src/main/java` e os testes em `src/test/java`, com nomes terminados em `Test`, e confiram:
   ```bash
   mvn -B verify
   ```

## Depois de ativar
Registrem em `docs/convencao-versionamento.md` os comandos usados e, nas instruções do agente, o que precisa passar para uma tarefa ser concluída.
