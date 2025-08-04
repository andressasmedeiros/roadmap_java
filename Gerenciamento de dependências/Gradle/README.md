# Gradle

## Projeto que utilizei gradle --> https://github.com/andressasmedeiros/cognizant-dev-week

O **Gradle** é uma ferramenta de automação de builds moderna e poderosa, utilizada principalmente para compilar, testar, empacotar e gerenciar dependências em projetos de software. Ele é amplamente utilizado em projetos Java, Android e outras linguagens suportadas.

---

## Para que serve?

- Automatiza o processo de **compilação** do código-fonte.
- Gerencia **dependências** de bibliotecas externas.
- Facilita a **execução de testes** automatizados.
- Cria pacotes executáveis (**.jar**, **.war**, etc.).
- Permite configurar **pipelines de build** personalizáveis.

---

## 🔧 Instalação

### 1️⃣ Pré-requisitos
- **Java JDK 8+** instalado e configurado ([Baixar aqui](https://adoptium.net/)).

### 2️⃣ Baixar o Gradle
- Acesse: [https://gradle.org/releases/](https://gradle.org/releases/)
- Baixe a versão **Binary-only** (arquivo `.zip`).

### 3️⃣ Extrair o arquivo
- Extraia o conteúdo para um diretório de sua preferência, por exemplo:
```
C:\Gradle
```

---

## ⚙️ Configuração da Variável de Ambiente (Windows)

1. Copie o caminho da pasta `bin` dentro da instalação do Gradle, exemplo:
```
C:\Gradle\gradle-8.8\bin
```

2. Pressione `Win + R`, digite:
```
sysdm.cpl
```
e pressione Enter.

3. Vá até **Configurações Avançadas do Sistema** → **Variáveis de Ambiente**.

<img width="934" height="596" alt="image" src="https://github.com/user-attachments/assets/e0e8be7e-5944-4475-bee6-9c03522fbda7" />


---

## Verificar Instalação

Abra o terminal (Prompt de Comando ou PowerShell) e execute:
```bash
gradle -v
```
Se a instalação estiver correta, será exibida a versão do Gradle instalada.

---

### 🔹 Observação
Você também pode usar o **Gradle Wrapper** (`gradlew`) fornecido por muitos projetos, que dispensa a instalação manual do Gradle no sistema.

## Exemplo de arquivo de configuração gradle:
```java
plugins {
	id 'java'
	id 'org.springframework.boot' version '3.3.5'
	id 'io.spring.dependency-management' version '1.1.7'
}

group = 'me.dio'
version = '0.0.1-SNAPSHOT'

java {
	toolchain {
		languageVersion = JavaLanguageVersion.of(17)
	}
}

repositories {
	mavenCentral()
}

dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
	implementation 'org.springframework.boot:spring-boot-starter-web'
	implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.5.0'

	runtimeOnly 'com.h2database:h2'
	runtimeOnly 'org.postgresql:postgresql'

	testImplementation 'org.springframework.boot:spring-boot-starter-test'
}

tasks.jar {
	manifest {
		attributes["Main-Class"] = "me.dio.CognizantDevWeekApplication"
	}
}

tasks.named('test') {
	useJUnitPlatform()
}
```
