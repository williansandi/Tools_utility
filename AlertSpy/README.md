# AlertSpy.dll para MetaTrader 4

A `AlertSpy.dll` é uma pequena mas poderosa utilidade que permite que um Expert Advisor (EA) ou script do MetaTrader 4 (MT4) leia o conteúdo de texto de uma janela de alerta padrão do MT4.

## 📖 Descrição

Esta DLL funciona encontrando a janela "Alerta" criada pelo MT4 e extraindo o texto da caixa de mensagem. Isso permite que um programa MQL4 capture e reaja a alertas baseados em texto de indicadores ou outros EAs que não fornecem integração direta por buffers ou variáveis.

A função principal `GetAlertBytes` é exportada para que possa ser importada e chamada de dentro de qualquer script MQL4.

## 🛠️ Como Compilar (Gerar a DLL)

Para compilar a `AlertSpy.dll` a partir do código-fonte, você precisará de:

*   **Visual Studio** (2019 ou 2022 recomendado).
*   A carga de trabalho (workload) **"Desenvolvimento para desktop com C++"** instalada no Visual Studio.

### Passos:

1.  **Abra a Solução:** Navegue até a pasta `AlertSpy.cpp` e abra o arquivo `AlertSpy.cpp.sln` com o Visual Studio.
2.  **Defina a Configuração de Build:** No topo do Visual Studio, mude a configuração da solução para **Release**.
3.  **Defina a Plataforma:** Mude a plataforma da solução para **Win32**. Isto é crucial, pois o MetaTrader 4 é uma aplicação de 32-bit.
4.  **Compile a Solução:** No menu, vá em `Build` -> `Build Solution` (ou `Compilar` -> `Compilar Solução`).
5.  **Encontre a DLL:** Se a compilação for bem-sucedida, a `AlertSpy.dll` compilada estará localizada na pasta `Lib\AlertSpy.cpp\Release`.

## 🚀 Como Usar no MQL4

1.  **Copie a DLL:** Copie o arquivo `AlertSpy.dll` gerado para a pasta `MQL4\Libraries` do diretório de dados do seu MetaTrader 4.
2.  **Importe no seu EA:** No seu Expert Advisor ou script MQL4, você precisa importar a função da DLL.

### Exemplo de Código MQL4:

```cpp
//--- Importa a função da DLL
#import "AlertSpy.dll"
int GetAlertBytes(char &buffer[], int buffer_size);
#import

//--- Buffer para guardar o texto do alerta
char alertTextBuffer[256];

//--- Na sua função OnTick() ou outra
void OnTick()
{
    // Limpa o buffer antes de chamar
    ArrayInitialize(alertTextBuffer, 0);

    // Chama a função da DLL
    int bytesCopied = GetAlertBytes(alertTextBuffer, 256);

    // Verifica se algum texto foi copiado
    if (bytesCopied > 0)
    {
        // Converte o array de char para uma string
        string alertMessage = CharArrayToString(alertTextBuffer);

        // Imprime a mensagem na aba "Experts"
        Print("Alert Spy capturou: ", alertMessage);

        // Agora você pode adicionar sua lógica baseada na alertMessage
        // if (StringFind(alertMessage, "BUY") >= 0) { ... }
    }
}
```
