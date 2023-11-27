# Inventario




### 1. **Definição de Requisitos e Escopo**
   - **Identifique os Itens de Configuração (ICs)**: Liste os tipos de ICs que você deseja rastrear (hardware, software, redes, documentos, serviços, etc.).
   - **Defina os Atributos dos ICs**: Determine quais informações você precisa rastrear para cada IC (por exemplo, modelo, número de série, localização, status, responsável).
   - **Funcionalidades Necessárias**: Pense em funcionalidades como rastreamento de mudanças, relatórios, alertas de manutenção, integrações com outras ferramentas, etc.

### 2. **Escolha da Plataforma**
   - **Google AppSheet**: É uma boa escolha para um rápido desenvolvimento e fácil manutenção.
   - **Outras Plataformas**: Avalie outras plataformas de desenvolvimento low-code/no-code se você tiver requisitos específicos que o AppSheet não possa atender.

### 3. **Design da Base de Dados**
   - **Estruture a Fonte de Dados**: Crie uma ou várias tabelas (por exemplo, em Google Sheets) para armazenar os dados dos ICs. Certifique-se de que a estrutura esteja clara e bem organizada.
   - **Relacionamentos entre Dados**: Se necessário, estabeleça relações entre diferentes tabelas (por exemplo, ICs e departamentos, ICs e tickets de suporte).

### 4. **Criação do Aplicativo**
   - **Conexão de Dados**: No AppSheet, conecte sua fonte de dados.
   - **Criação de Views**: Desenvolva diferentes visualizações para diferentes tipos de usuários (técnicos de TI, gerentes, suporte, etc.).
   - **Funcionalidades Personalizadas**: Implemente funções para adicionar, editar e deletar registros, além de visualizar relatórios e alertas.

### 5. **Teste e Feedback**
   - **Teste Interno**: Use o aplicativo internamente para identificar bugs ou melhorias necessárias.
   - **Coleta de Feedback**: Obtenha feedback dos usuários para entender o que pode ser melhorado.

### 6. **Implantação e Treinamento**
   - **Lançamento Oficial**: Após ajustes, lance o aplicativo para os usuários finais.
   - **Treinamento e Documentação**: Forneça treinamento e documentação adequados para garantir que todos possam usar o aplicativo eficientemente.

### 7. **Manutenção e Atualização Contínua**
   - **Monitoramento**: Monitore o uso do aplicativo e colete dados sobre seu desempenho.
   - **Atualizações Regulares**: Faça atualizações com base no feedback contínuo e nas mudanças nas necessidades de negócios.

### Dicas Adicionais
- **Integrações**: Considere integrar seu aplicativo com outras ferramentas usadas em sua organização (como sistemas de ticketing).
- **Segurança e Controle de Acesso**: Estabeleça níveis de acesso e controles de segurança para proteger as informações sensíveis.
- **Escalabilidade**: Projete a aplicação pensando na escalabilidade para lidar com o crescimento da organização e o aumento no número de ICs.


https://chat.openai.com/share/325c8673-aab2-4d0b-8b9e-c7ff59da0f76

--------------

```mermaid
erDiagram
    MUDANCAS ||--o{ SERVIDORES : "relacionado a"
    MUDANCAS ||--o{ IPS : "relacionado a"
    MUDANCAS ||--o{ REDES : "relacionado a"
    MUDANCAS ||--o{ SERVICOS : "relacionado a"
    MUDANCAS ||--o{ PORTAS : "relacionado a"
    MUDANCAS ||--o{ LOGS : "relacionado a"
    MUDANCAS ||--o{ CONFIGURACAO : "relacionado a"
    MUDANCAS ||--o{ APLICACOES : "relacionado a"
    MUDANCAS ||--o{ CONTATOS : "relacionado a"
    SERVIDORES ||--o{ SERVICOS : "contém"
    SERVIDORES ||--o{ PORTAS : "contém"
    SERVIDORES ||--o{ LOGS : "contém"
    SERVIDORES ||--o{ APLICACOES : "contém"
    SERVIDORES ||--o{ CONFIGURACAO : "contém"
    SERVIDORES ||--o{ CONTATOS : "contém"
    IPS ||--o{ REDES : "relacionado a"
    IPS ||--o{ CONTATOS : "relacionado a"
    IPS ||--o{ SERVIDORES : "relacionado a"
    IPS ||--o{ CONTATOS : "contém"
    REDES ||--o{ CONTATOS : "contém"
    SERVICOS ||--o{ REPOSITORIOS : "contém"
    SERVICOS ||--o{ CONFIGURACAO : "contém"
    SERVICOS ||--o{ CONTATOS : "contém"
    PORTAS ||--o{ CONTATOS : "contém"
    LOGS ||--o{ CAMINHO : "contém"
    CONFIGURACAO ||--o{ APLICACOES : "relacionado a"
    CONFIGURACAO ||--o{ MANUAIS : "relacionado a"
    CONFIGURACAO ||--o{ CONTATOS : "contém"
    APLICACOES ||--o{ REPOSITORIOS : "contém"
    APLICACOES ||--o{ MANUAIS : "contém"
    APLICACOES ||--o{ CONTATOS : "contém"
    CONTATOS ||--o{ DETALHES : "contém"

    MUDANCAS {
        int ID
        string Tipo
        string Descricao
        int ID_Servidor
        int ID_IP
        int ID_Rede
        int ID_Servico
        int ID_Porta
        int ID_Log
        int ID_Configuracao
        int ID_Aplicacao
        string Chamado
        int ID_Contato
    }
    SERVIDORES {
        int ID
        string Nome
        string Local
        int ID_Servico
        int ID_Porta
        int ID_Logs
        int ID_Aplicacao
        int ID_Configuracao
        int ID_Contato
    }
    IPS {
        int ID
        string Endereco-IP
        int ID_Rede
        int ID_Contato
        int ID_Servidor
    }
    REDES {
        int ID
        string Nome
        string Tipo
        string Local
        string Descricao
        int ID_Contato
    }
    SERVICOS {
        int ID
        string Nome
        string Repositorios
        int ID_Configuracao
        int ID_Contato
    }
    PORTAS {
        int ID
        string Numero
        string Descricao
    }
    LOGS {
        int ID
        string Descricao
        string Caminho
    }
    CONFIGURACAO {
        int ID
        int ID_Aplicacao
        string Nome
        string Manual
    }
    APLICACOES {
        int ID
        string Nome
        string Repositorio
        string Manual
        int ID_Contato
    }
    CONTATOS {
        int ID
        string Nome
        string Numero-de-Telefone
        string Email
        string Empresa
        string Responsabilidade
        string Nivel
        string Servico
        string IP
        string Porta
        string Rede
        string Configuracao
    }
```

### Entidades e Atributos

1. **MUDANÇAS**
   - Atributos: ID, Tipo, Descrição, ID_Servidor, ID_IP, ID_Rede, ID_Serviço, ID_Porta, ID_Log, ID_Configuração, ID_Aplicação, Chamado, ID_Contato

2. **SERVIDORES**
   - Atributos: ID, Nome, Local, ID_Serviço, ID_Porta, ID_Logs, ID_Aplicação, ID_Configuração, ID_Contato

3. **IPS**
   - Atributos: ID, Endereço-IP, ID_Rede, ID_Contato, ID_Servidor

4. **REDES**
   - Atributos: ID, Nome, Tipo, Local, Descrição, ID_Contato

5. **SERVIÇOS**
   - Atributos: ID, Nome, Repositórios, ID_Configuração, ID_Contato

6. **PORTAS**
   - Atributos: ID, Número, Descrição

7. **LOGS**
   - Atributos: ID, Descrição, Caminho

8. **CONFIGURAÇÃO**
   - Atributos: ID, ID_Aplicação, Nome, Manual

9. **APLICAÇÕES**
   - Atributos: ID, Nome, Repositório, Manual, ID_Contato

10. **CONTATOS**
    - Atributos: ID, Nome, Número-de-Telefone, Email, Empresa, Responsabilidade, Nível, Serviço, IP, Porta, Rede, Configuração

### Relações

- **MUDANÇAS** está relacionado a várias entidades, como SERVIDORES, IPS, REDES, SERVIÇOS, PORTAS, LOGS, CONFIGURAÇÃO, APLICAÇÕES e CONTATOS.
- **SERVIDORES** contém SERVIÇOS, PORTAS, LOGS, APLICAÇÕES, CONFIGURAÇÃO e CONTATOS.
- **IPS** está relacionado a REDES, CONTATOS e SERVIDORES.
- **REDES** contém CONTATOS.
- **SERVIÇOS** contém REPOSITÓRIOS, CONFIGURAÇÃO e CONTATOS.
- **PORTAS** contém CONTATOS.
- **LOGS** contém CAMINHO.
- **CONFIGURAÇÃO** está relacionada a APLICAÇÕES e MANUAIS, e contém CONTATOS.
- **APLICAÇÕES** contém REPOSITÓRIOS, MANUAIS e CONTATOS.
- **CONTATOS** contém DETALHES.

https://chat.openai.com/share/39208bf0-32db-43ce-8b7d-53288cd17d82

-----------

