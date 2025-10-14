| **Tipo**      | **Quando usar**                                                                                      | **Exemplo**                                                      |
| ------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **feat:**     | Para **nova funcionalidade** no sistema.                                                             | `feat: adicionar módulo de relatórios financeiros`               |
| **fix:**      | Para **correção de bug** ou comportamento inesperado.                                                | `fix: corrigir cálculo de quilometragem no dashboard`            |
| **chore:**    | Para mudanças de **manutenção** que não afetam o usuário final (infra, build, upgrade de libs).      | `chore: migrar solução para .NET 9`                              |
| **refactor:** | Para mudanças de **código internas** que não alteram o comportamento (limpeza, melhorias de design). | `refactor: extrair lógica de validação para um serviço separado` |
| **docs:**     | Para mudanças em **documentação** apenas.                                                            | `docs: atualizar README com instruções de deploy`                |
| **style:**    | Para mudanças de **formatação ou estilo**, sem alterar comportamento.                                | `style: aplicar formatação padrão com dotnet format`             |
| **test:**     | Para **criação ou atualização de testes automatizados**.                                             | `test: adicionar testes de integração para API de viagens`       |
| **build:**    | Para mudanças que afetam o **sistema de build ou dependências**.                                     | `build: atualizar pacotes NuGet para versão 9.x`                 |
| **ci:**       | Para ajustes no **pipeline de integração contínua**.                                                 | `ci: adicionar workflow de build no GitHub Actions`              |
| **perf:**     | Para mudanças de código que **melhoram performance**.                                                | `perf: otimizar query de listagem de veículos`                   |
| **revert:**   | Para **reverter** um commit anterior.                                                                | `revert: reverter alteração no cálculo de frete (#123)`          |

