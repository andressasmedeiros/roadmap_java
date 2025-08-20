# JUnit – Framework de Testes para Java

## O que é?
JUnit é um **framework de testes unitários** para Java, usado para verificar se o código funciona corretamente de forma automatizada.

[Projeto que usei Junit](https://github.com/andressasmedeiros/teste_pratico_iniflex)
---

## Principais características
- Escrita e execução de **testes automatizados**.
- Integração com **IDEs** (Eclipse, IntelliJ, VS Code) e **build tools** (Maven, Gradle).
- Uso de **anotações**:
  - `@Test` → define um método de teste.
  - `@BeforeEach` e `@AfterEach` → código antes/depois de cada teste.
  - `@BeforeAll` e `@AfterAll` → código antes/depois de todos os testes.
- **Asserções**: verificam os resultados (`assertEquals`, `assertTrue`, etc.).
- Apoia práticas como **TDD (Test-Driven Development)**.

---

## Exemplo simples (JUnit 5)
```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class CalculadoraTest {

    @Test
    void somaDeDoisNumeros() {
        Calculadora calc = new Calculadora();
        int resultado = calc.somar(2, 3);
        assertEquals(5, resultado);
    }
}
```

---

## Integrações e usos avançados
- **Maven/Gradle** → adicione a dependência do JUnit e execute os testes automaticamente na pipeline de build.
- **CI/CD (Integração Contínua)** → junto com ferramentas como Jenkins, GitHub Actions ou GitLab CI, os testes podem rodar a cada commit.
- **Test Coverage** → frameworks como **JaCoCo** podem ser usados com JUnit para medir a cobertura dos testes.
- **Mocking** → normalmente o JUnit é usado junto com frameworks como **Mockito** para simular dependências externas (bancos de dados, APIs etc.).

---

## Boas práticas com JUnit
- Escreva testes **pequenos e específicos** (um caso por teste).
- Nomeie métodos de teste de forma clara (`somaDeDoisNumeros_DeveRetornarResultadoCorreto`).
- Use **assertivas significativas** (não apenas `assertTrue`).
- Evite **lógica complexa** dentro dos testes → o teste deve ser simples e direto.
- Combine com **TDD**: escreva primeiro o teste, depois o código.

---

## Por que usar?
- Aumenta a **confiabilidade** do código.
- Evita **regressões** em novas versões.
- Facilita a **manutenção** e evolução do software.
- Permite aplicar boas práticas de **TDD**.


---
# Mockito – Framework de Mocking para Java

## O que é?
O Mockito é um **framework de mocking para Java**, usado para **criar objetos simulados** em testes.  
Ele é normalmente utilizado junto com o **JUnit** para testar partes isoladas do código sem depender de componentes externos como bancos de dados, APIs ou serviços.

---

## O que ele faz?
- Cria **mocks** (objetos falsos que imitam o comportamento de classes reais).  
- Permite **simular respostas** de métodos de dependências externas.  
- **Verifica interações** → checa se métodos foram chamados, quantas vezes e com quais parâmetros.  
- Facilita a escrita de **testes unitários isolados**, sem necessidade de configurar um ambiente completo.  

---

## Exemplo simples com Mockito + JUnit 5

```java
import static org.mockito.Mockito.*;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class ServicoEmail {
    public boolean enviar(String destinatario, String mensagem) {
        // Lógica real de envio de e-mail
        return true;
    }
}

class Notificador {
    private final ServicoEmail servicoEmail;

    public Notificador(ServicoEmail servicoEmail) {
        this.servicoEmail = servicoEmail;
    }

    public boolean notificar(String usuario, String msg) {
        return servicoEmail.enviar(usuario, msg);
    }
}

public class NotificadorTest {

    @Test
    void deveNotificarUsuarioComSucesso() {
        // Criando um mock do serviço de e-mail
        ServicoEmail servicoEmailMock = mock(ServicoEmail.class);

        // Definindo o comportamento simulado
        when(servicoEmailMock.enviar("teste@dominio.com", "Olá!"))
            .thenReturn(true);

        // Classe em teste
        Notificador notificador = new Notificador(servicoEmailMock);

        // Executa o método e valida o resultado
        boolean resultado = notificador.notificar("teste@dominio.com", "Olá!");
        assertTrue(resultado);

        // Verifica se o método enviar foi chamado uma vez com os parâmetros corretos
        verify(servicoEmailMock, times(1))
            .enviar("teste@dominio.com", "Olá!");
    }
}
```

---

## Por que usar o Mockito?
- Evita dependência de **infraestrutura real** (banco de dados, rede, API).  
- Permite testes **rápidos e isolados**.  
- Garante que o código seja testado mesmo quando os serviços externos não estão disponíveis.  
- Facilita a aplicação de **TDD**.  

---

## Resumindo
O Mockito é o **parceiro ideal do JUnit** para criar **testes unitários isolados**, simulando dependências externas e verificando interações.
