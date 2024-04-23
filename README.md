# Criando-Testes-Automatizados-de-UI-em-Android-com-Kotlin-e-Espresso

**Criando Testes Automatizados de UI em Android com Kotlin e Espresso**

O desenvolvimento de testes automatizados de UI é fundamental para garantir a qualidade e a robustez de um aplicativo Android. O Espresso é uma biblioteca de teste amplamente utilizada para criar e executar testes de interface do usuário no Android. Vamos explorar como criar testes automatizados de UI usando Kotlin e Espresso:

1. **Configuração do Ambiente:**
   - Certifique-se de ter o Android Studio instalado.
   - Crie um novo projeto Android ou utilize um projeto existente.
   - Adicione as dependências necessárias para o Espresso no arquivo `build.gradle`.

2. **Espresso Basics:**
   - O Espresso é baseado em ações e verificações.
   - Ações são interações do usuário, como clicar em botões, preencher campos de texto, etc.
   - Verificações são usadas para verificar se os elementos da interface do usuário estão corretos após a execução de uma ação.

3. **Escrevendo Testes:**
   - Crie classes de teste para cada tela ou funcionalidade do aplicativo.
   - Use a classe `Espresso` para realizar ações e verificações.
   - Exemplo de teste para verificar se um botão está visível e clicável:

```kotlin
@Test
fun testButtonVisibilityAndClickability() {
    // Encontra o botão pelo ID
    onView(withId(R.id.myButton))
        .check(matches(isDisplayed())) // Verifica se está visível
        .perform(click()) // Clica no botão
}
```

4. **Cenários de Teste:**
   - Desenvolva cenários de teste para diferentes fluxos do aplicativo.
   - Por exemplo, teste o processo de login, preenchimento de formulários, navegação entre telas, etc.

5. **Testes de Integração:**
   - Além dos testes de UI, crie testes de integração para verificar a comunicação entre componentes do aplicativo.
   - Use o Espresso para simular ações do usuário e verificar os resultados.

6. **Executando os Testes:**
   - Execute os testes no emulador ou dispositivo físico.
   - Utilize o Android Test Orchestrator para gerenciar a execução dos testes.

Lembre-se de manter seus testes atualizados à medida que o aplicativo evolui. Testes automatizados de UI são essenciais para garantir que seu aplicativo funcione corretamente em diferentes dispositivos e cenários.

Apresentando um exemplo básico de teste completo usando Espresso. Vamos criar um teste para verificar se um botão está visível e clicável em uma atividade Android. Lembre-se de que, na prática, você adaptará esses conceitos para o seu próprio projeto.

1. **Configuração do Ambiente:**
   - Certifique-se de ter o Android Studio instalado.
   - Crie um novo projeto Android ou utilize um projeto existente.
   - Adicione as dependências necessárias para o Espresso no arquivo `build.gradle`.

2. **Estrutura de Testes:**
   - No Android, os testes são organizados em duas pastas: `test` (para testes unitários) e `androidTest` (para testes instrumentados).
   - Para testes de interface do usuário (UI), usaremos a pasta `androidTest`.

3. **Criando um Teste Instrumentado:**
   - Crie uma classe de teste para a atividade que você deseja testar. Por exemplo, se sua atividade se chama `MainActivity`, crie uma classe chamada `MainActivityTest`.
   - Use a anotação `@RunWith(AndroidJUnit4.class)` para indicar que estamos executando testes instrumentados.
   - Defina uma regra (`@Rule`) para a atividade que será testada:

```kotlin
@RunWith(AndroidJUnit4::class)
class MainActivityTest {

    @get:Rule
    val activityRule = ActivityTestRule(MainActivity::class.java)

    @Test
    fun testButtonVisibilityAndClickability() {
        // Encontra o botão pelo ID
        onView(withId(R.id.myButton))
            .check(matches(isDisplayed())) // Verifica se está visível
            .perform(click()) // Clica no botão
    }
}
```

4. **Explicação do Código:**
   - `@RunWith(AndroidJUnit4::class)` indica que estamos usando o AndroidJUnitRunner para executar os testes.
   - `@get:Rule` define a regra para a atividade (`MainActivity`).
   - No método `testButtonVisibilityAndClickability()`, usamos o `onView()` para encontrar o botão com o ID `myButton`.
   - `check(matches(isDisplayed()))` verifica se o botão está visível na tela.
   - `perform(click())` simula um clique no botão.

5. **Robot Pattern (Opcional):**
   - Para manter a estrutura organizada, você pode criar uma classe "Robot" para encapsular as asserções e interações com a UI. Isso torna o teste mais legível e modular.

```kotlin
class MainActivityRobot {

    fun clickMyButton() {
        onView(withId(R.id.myButton)).perform(click())
    }

    fun assertMyButtonIsVisible() {
        onView(withId(R.id.myButton)).check(matches(isDisplayed()))
    }
}

// Na classe de teste:
@Test
fun testButtonVisibilityAndClickability() {
    MainActivityRobot().apply {
        assertMyButtonIsVisible()
        clickMyButton()
    }
}
```

Lembre-se de adaptar esses conceitos ao seu projeto específico. O Espresso é uma ferramenta poderosa para testar a interface do usuário no Android, e seguir boas práticas garantirá testes mais robustos e eficazes.

https://developer.android.com/training/testing/espresso

https://jakewharton.com/testing-robots/

https://developer.android.com/training/testing
