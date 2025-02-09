## 🗂️ Script Python para Renomeação de Pastas e União de PDFs

## 📝 Descrição do Projeto

Este é um script Python desenvolvido para automatizar tarefas comuns em fluxos de trabalho de digitalização de documentos. O script executa duas funções principais:

1.  **Renomeia Pastas:**  Remove espaços dos nomes de pastas dentro de um diretório específico, substituindo-os por underscores (`_`). Isso pode ser útil para evitar problemas com espaços em nomes de pastas em sistemas de arquivos e scripts posteriores.
2.  **Une Arquivos PDF:** Dentro de cada pasta (após a renomeação), o script procura por arquivos com a extensão `.pdf`. Ele então os une em um único arquivo PDF, seguindo uma lógica de ordenação baseada nos nomes dos arquivos para garantir a sequência correta no PDF final.

Este script é especialmente útil para organizar e consolidar documentos digitalizados que são frequentemente armazenados em pastas separadas e como arquivos PDF individuais.

### Requisitos:

|           | Versão Recomendada |
|-----------|--------------------|
| Python:   | 3.6 ou superior    |
| PyPDF2:  | Última versão      |
| Módulos Python Padrão: | `os`, `getpass`, `re` (já incluídos na instalação padrão do Python) |


### 🛠️ Funcionalidades:

O script executa as seguintes etapas:

1.  **Obtém o Nome de Usuário:** Utiliza o módulo `getpass` para obter o nome do usuário que está executando o script, tornando-o independente da configuração específica do sistema.
2.  **Define o Caminho do Diretório "Digitalizacao":**  Assume que os arquivos e pastas a serem processados estão localizados dentro de um diretório chamado "Digitalizacao" na área de trabalho (Desktop) do usuário atual. Este caminho pode ser facilmente modificado no código.
3.  **Renomeia Pastas no Diretório "Digitalizacao":**
    *   Lista todas as pastas e arquivos dentro do diretório "Digitalizacao".
    *   Itera sobre cada item.
    *   Verifica se o item é um diretório e se o seu nome contém espaços.
    *   Se ambas as condições forem verdadeiras, o script renomeia o diretório, substituindo todos os espaços no nome por underscores (`_`).
4.  **Une Arquivos PDF Dentro de Cada Pasta:**
    *   Após a renomeação (ou caso as pastas já estejam renomeadas), o script itera sobre cada pasta dentro do diretório "Digitalizacao".
    *   Para cada pasta:
        *   Lista todos os arquivos dentro da pasta.
        *   Filtra a lista para incluir apenas arquivos com a extensão `.pdf`.
        *   Extrai informações de ordenação dos nomes dos arquivos PDF, procurando por padrões como:
            *   Números dentro de parênteses, por exemplo, "Arquivo (1).pdf" ou "Página (1-5).pdf".
            *   A palavra "capa" (para arquivos de capa que devem vir no início).
        *   Ordena os arquivos PDF com base nas informações extraídas (arquivos "capa" primeiro, seguidos por arquivos numerados em ordem crescente).
        *   Utiliza a biblioteca `PyPDF2` para unir os arquivos PDF ordenados em um único arquivo PDF.
        *   O arquivo PDF unido é salvo no diretório "Digitalizacao" com o mesmo nome da pasta correspondente (antes da substituição de espaços por underscores, se aplicável).

#### Objetivos Funcionais

*   **Automatização:** Automatizar o processo de renomeação de pastas e união de arquivos PDF, economizando tempo e reduzindo erros manuais em fluxos de trabalho de digitalização.
*   **Manipulação do Sistema de Arquivos:**  Utilizar o módulo `os` do Python para realizar operações no sistema de arquivos, como listar diretórios, verificar se um item é um diretório e renomear pastas.
*   **Processamento de PDFs:** Empregar a biblioteca `PyPDF2` para ler, manipular e unir arquivos PDF de forma programática.
*   **Lógica de Ordenação Flexível:** Implementar uma lógica de ordenação de arquivos PDF baseada em convenções de nomenclatura comuns, permitindo flexibilidade na organização dos documentos digitais.

### 🧷 Trabalhos Futuros:

*   **Tratamento de Erros Robusto:** Implementar tratamento de erros mais abrangente usando blocos `try...except` para lidar com situações como arquivos PDF inválidos, arquivos não encontrados, erros de permissão, etc., tornando o script mais resiliente.
*   **Lógica de Ordenação Aprimorada:** Refinar a lógica de extração de informações de ordenação dos nomes de arquivos PDF para suportar uma variedade maior de convenções de nomenclatura e casos complexos. Considerar a possibilidade de utilizar outras informações para ordenação, como metadados ou datas de modificação dos arquivos.
*   **Personalização do Caminho e Nome do Arquivo de Saída:** Permitir que o usuário personalize o caminho do diretório "Digitalizacao" e o nome dos arquivos PDF de saída através de argumentos de linha de comando ou um arquivo de configuração.
*   **Logging Detalhado:** Adicionar logging para registrar as etapas de execução do script, avisos e erros em um arquivo de log, facilitando o monitoramento e a depuração.
*   **Opção para Deletar Arquivos Originais:** Implementar uma opção (configurável pelo usuário) para deletar os arquivos PDF originais após a união ser concluída, para ajudar a organizar o diretório "Digitalizacao".
*   **Manipulações Avançadas de PDF:** Expandir as funcionalidades para incluir manipulações mais avançadas de PDF usando `PyPDF2.PdfWriter`, como inserção de páginas em posições específicas, reordenação de páginas, rotação, etc.
*   **Interface de Linha de Comando (CLI):** Desenvolver uma interface de linha de comando mais completa para o script, facilitando a execução e a personalização por usuários menos técnicos.

**Observação:** Este script está em constante desenvolvimento e pode ser aprimorado com novas funcionalidades e melhorias para atender a diferentes necessidades de automatização de fluxos de trabalho de digitalização.

### 🫡 Contribuições:

Contribuições são bem-vindas! Se você encontrar algum bug, tiver sugestões de melhoria, ou quiser propor novas funcionalidades para o script, por favor, abra um "issue" neste repositório ou envie um "pull request" com suas alterações.

### 🔓 Licença:

Este projeto está licenciado sob a licença MIT.