# missao-da-semana-aula-4
✅ 1. Problema escolhido

Criar uma função em Python para validar se um e-mail é válido.

❌ 2. Primeira iteração (vaga) + resposta ruim
Prompt vago:

"Faça um código em Python para validar email"

Resposta ruim:
def validar(email):
    return "@" in email
Problemas:
Não valida formato corretamente
Aceita emails inválidos (@, abc@, @teste)
Não segue boas práticas
Sem documentação
Sem testes
⚙️ 3. Aplicando a Equação do Prompt
🧠 Prompt estruturado:
Persona: Você é um engenheiro de software sênior especializado em Python.
Contexto: Estou criando uma API e preciso validar emails corretamente.
Restrições:
Usar regex
Seguir boas práticas (PEP8)
Incluir docstring
Criar exemplos de uso
Formato: Código Python bem documentado
Prompt resultante:

"Você é um engenheiro de software sênior especializado em Python. Estou criando uma API e preciso validar emails corretamente. Crie uma função em Python que valide emails usando regex. Siga PEP8, inclua docstring e exemplos de uso."

🔄 4. Iteração intermediária (melhor, mas ainda incompleta)
import re

def validar_email(email: str) -> bool:
    """
    Valida se um email está em formato correto.

    :param email: Email a ser validado
    :return: True se válido, False caso contrário
    """
    padrao = r'^[\w\.-]+@[\w\.-]+\.\w+$'
    return bool(re.match(padrao, email))
Melhorias:

✔ Usa regex
✔ Tem docstring
✔ Tipagem

Problemas ainda:
Regex simplificada (não cobre todos os casos válidos)
Sem testes
Sem tratamento de erros
Sem exemplos práticos
🚀 5. Iteração final (resultado ideal)
Versão em Markdown
## Função: validar_email

Valida se uma string possui formato de e-mail válido.

### Requisitos
- Python 3.8+
- Biblioteca padrão (`re`)

### Implementação

```python
import re
from typing import Pattern

EMAIL_REGEX: Pattern = re.compile(
    r"(^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$)"
)

def validar_email(email: str) -> bool:
    """
    Valida se um e-mail possui formato válido.

    Args:
        email (str): Endereço de e-mail a ser validado.

    Returns:
        bool: True se o e-mail for válido, False caso contrário.

    Examples:
        >>> validar_email("teste@email.com")
        True
        >>> validar_email("email_invalido")
        False
    """
    if not isinstance(email, str):
        raise TypeError("O email deve ser uma string")

    return bool(EMAIL_REGEX.match(email))
Exemplos de uso
emails = [
    "user@example.com",
    "invalido@",
    "@teste.com",
    "valido123@gmail.com"
]

for e in emails:
    print(e, validar_email(e))
Testes básicos
def test_validar_email():
    assert validar_email("user@test.com")
    assert not validar_email("user@test")
    assert not validar_email("@test.com")

---

## Versão em **YAML (documentação estruturada)**

```yaml
funcao: validar_email
descricao: Valida se uma string possui formato de e-mail válido

linguagem: python
versao_minima: "3.8"

dependencias:
  - re

assinatura: "validar_email(email: str) -> bool"

validacoes:
  - tipo: string obrigatoria
  - formato: regex

regex: "^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\\.[a-zA-Z0-9-.]+$"

erros:
  - tipo: TypeError
    condicao: entrada nao eh string

exemplos:
  - entrada: "teste@email.com"
    saida: true
  - entrada: "invalido@"
    saida: false

testes:
  - nome: email_valido
    entrada: "user@test.com"
    esperado: true
  - nome: email_invalido_sem_dominio
    entrada: "user@test"
    esperado: false
  - nome: email_invalido_sem_usuario
    entrada: "@test.com"
    esperado: false
🧩 Conclusão

Você pode ver claramente a evolução:

Prompt vago → código inútil
Prompt estruturado → solução funcional
Refinamento → solução robusta, documentada e testável
<img width="1003" height="557" alt="Captura de tela 2026-03-23 191940" src="https://github.com/user-attachments/assets/cbc88f23-0295-4804-ab15-485b0a618b99" />

