# Swagger

## Projetos que utilizei Swagger
- https://github.com/andressasmedeiros/cognizant-dev-week
- https://github.com/andressasmedeiros/gerenciamento_farmacia/tree/main/api

## O que é Swagger
- É um conjunto de ferramentas de software e uma especificação aberta para descrever e documentar APIs REST, facilitando o design, contrução, documentação e consumo de APIs. Originalmente chamado de Swagger, o projeto evoluiu e a especificação passou a ser chamada OpenAPI Specification (OAS), enquanto o termo Swagger passou a designar o conjunto de ferramentas que implementam essa especificação.

## Configurando no seu projeto SpringBoot
### Maven
- Adicione no seu arquivo pom.xml:
```java
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.5.0</version>
</dependency>
```
### Gradle
- Adicione no seu arquivo build.gradle:
```java
implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.5.0'
```

- O Springdoc já detecta automaticamente os endpoints do seu projeto, então normalmente não é necessário nenhuma configuração adicional.
Mas você pode adicionar um bean de configuração para personalizar informações da sua API:
```java
import io.swagger.v3.oas.models.OpenAPI;
import io.swagger.v3.oas.models.info.Info;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class SwaggerConfig {

    @Bean
    public OpenAPI customOpenAPI() {
        return new OpenAPI()
                .info(new Info()
                        .title("Minha API")
                        .description("Documentação da API usando Swagger/OpenAPI")
                        .version("1.0.0"));
    }
}
```

- Para acessar a documentação basta acessar = http://localhost:8080/swagger-ui.html

## Sua interface é como da imagem abaixo:
<img width="1892" height="904" alt="thumb_backend" src="https://github.com/user-attachments/assets/c3d5d338-13c3-462b-94d6-5f0a1dc80bab" /><br>

## Segue um vídeo testando endpoints
[🎥 Assista à demonstração no Drive](https://drive.google.com/file/d/1YLUmM2_hbUSQ9qiWo-keOiV23zouS8zV/view?usp=sharing)

# Principais comandos no Spring Boot
- @Operation
  > Descreve o propósito de um endpoint (título, resumo, descrição, tags, etc.).
```java
@Operation(
    summary = "Busca um usuário pelo ID",
    description = "Retorna os detalhes do usuário com base no ID informado",
    tags = {"Usuários"}
)
```

- @Parameter
   > Documenta um parâmetro de entrada do endpoint (query, path, header, cookie).
```java
@Parameter(
    name = "id",
    description = "ID do usuário",
    required = true
)
@PathVariable Long id

```

- @RequestBody
   > Documenta o corpo da requisição.
```java
@io.swagger.v3.oas.annotations.parameters.RequestBody(
    description = "Dados do novo usuário",
    required = true
)
```

- @ApiResponse
  > Define respostas possíveis para um endpoint.
```java
@ApiResponses({
    @ApiResponse(responseCode = "200", description = "Usuário encontrado com sucesso"),
    @ApiResponse(responseCode = "404", description = "Usuário não encontrado"),
    @ApiResponse(responseCode = "500", description = "Erro interno do servidor")
})

```

- @Schema
  > Usada em modelos (DTOs) para descrever campos.
```java
@Schema(description = "Nome completo do usuário", example = "Maria Silva")
private String nome;

```
- @ArraySchema
  > Descreve arrays em respostas ou parâmetros.
```java
@ArraySchema(schema = @Schema(implementation = UsuarioDTO.class))
```

- @Hidden
  > Oculta um endpoint ou campo específico da documentação Swagger.

---

## Exemplo de código com Swagger

```java
package com.example.demo.controller;

import com.example.demo.model.UsuarioDTO;
import io.swagger.v3.oas.annotations.Operation;
import io.swagger.v3.oas.annotations.Parameter;
import io.swagger.v3.oas.annotations.responses.ApiResponse;
import io.swagger.v3.oas.annotations.responses.ApiResponses;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.Arrays;
import java.util.List;

@RestController
@RequestMapping("/usuarios")
public class UsuarioController {

    @Operation(summary = "Lista todos os usuários", tags = {"Usuários"})
    @ApiResponse(responseCode = "200", description = "Lista retornada com sucesso")
    @GetMapping
    public List<UsuarioDTO> listar() {
        return Arrays.asList(
                new UsuarioDTO(1L, "Maria Silva", "maria@email.com"),
                new UsuarioDTO(2L, "João Santos", "joao@email.com")
        );
    }

    @Operation(summary = "Busca um usuário pelo ID", tags = {"Usuários"})
    @ApiResponses({
        @ApiResponse(responseCode = "200", description = "Usuário encontrado"),
        @ApiResponse(responseCode = "404", description = "Usuário não encontrado")
    })
    @GetMapping("/{id}")
    public ResponseEntity<UsuarioDTO> buscarPorId(
            @Parameter(description = "ID do usuário", required = true)
            @PathVariable Long id) {
        return ResponseEntity.ok(new UsuarioDTO(id, "Maria Silva", "maria@email.com"));
    }

    @Operation(summary = "Cria um novo usuário", tags = {"Usuários"})
    @ApiResponse(responseCode = "201", description = "Usuário criado com sucesso")
    @PostMapping
    public ResponseEntity<UsuarioDTO> criar(@RequestBody UsuarioDTO usuarioDTO) {
        usuarioDTO.setId(3L);
        return ResponseEntity.status(HttpStatus.CREATED).body(usuarioDTO);
    }
}
```
