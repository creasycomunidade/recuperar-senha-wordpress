# 🔐 Recuperar Senha WordPress

**Uma ferramenta simples, gratuita e open source para recuperar o acesso e redefinir senhas de usuários do WordPress diretamente pela hospedagem.**

Desenvolvido e disponibilizado pela **CREASY Comunidade**.

![License](https://img.shields.io/badge/License-MIT-green.svg)
![PHP](https://img.shields.io/badge/PHP-MySQL-blue.svg)
![WordPress](https://img.shields.io/badge/WordPress-Password%20Recovery-21759B.svg)
![Open Source](https://img.shields.io/badge/Open%20Source-Free-orange.svg)

## 📖 Sobre o projeto

O **Recuperar Senha WordPress** é uma pequena ferramenta desenvolvida em PHP para auxiliar administradores de sites, desenvolvedores e profissionais de suporte técnico na recuperação de acesso a instalações WordPress.

Esqueceu a senha do administrador? Está sem acesso ao painel do WordPress, mas ainda possui acesso à hospedagem?

Esta ferramenta permite visualizar os usuários cadastrados no banco de dados do WordPress e redefinir suas senhas por meio de uma interface web.

Não é necessário acessar o painel administrativo do WordPress, mas é indispensável ter acesso autorizado à hospedagem.

> ⚠️ **Aviso:** a versão atual é uma ferramenta de manutenção emergencial, sem autenticação própria. Não deve ficar acessível publicamente em servidores de produção. Utilize somente em ambientes autorizados, com restrição de acesso, e remova os arquivos após o procedimento.

## ✨ Funcionalidades

- ✅ Listagem dos usuários cadastrados no WordPress.
- ✅ Exibição de ID, nome de usuário e e-mail.
- ✅ Seleção de usuários para redefinição de senha.
- ✅ Formulário de alteração de senha.
- ✅ Conexão com o banco de dados utilizando as configurações do WordPress.
- ✅ Interface web simples e responsiva.
- ✅ Não exige acesso ao painel `/wp-admin`.
- ✅ Código aberto e disponível gratuitamente.

## 📋 Requisitos

Antes de começar, você precisará de:

- Uma instalação WordPress existente.
- Acesso autorizado à hospedagem.
- Gerenciador de arquivos, FTP ou SFTP.
- Servidor com PHP e extensão MySQLi.
- Banco de dados MySQL ou MariaDB.
- Arquivo `wp-config.php` configurado corretamente.

**Importante:** a versão atual consulta diretamente a tabela `wp_users`. Se sua instalação utilizar outro prefixo de tabelas, será necessário adaptar as consultas do código.

## 📥 Download

Acesse o repositório oficial:

**https://github.com/creasycomunidade/recuperar-senha-wordpress**

Você pode baixar os arquivos clicando em:

**Code → Download ZIP**

Ou clonar o repositório:

```bash
git clone https://github.com/creasycomunidade/recuperar-senha-wordpress.git
```

## 🚀 Instalação passo a passo

### 1. Acesse sua hospedagem

Entre no painel da hospedagem onde o WordPress está instalado.

Você pode utilizar:

- Gerenciador de Arquivos do cPanel ou painel equivalente.
- FTP.
- SFTP.
- SSH, quando disponível.

Localize a pasta raiz do site.

Em hospedagens tradicionais, geralmente ela se chama:

```text
public_html/
```

### 2. Crie uma pasta na raiz do site

Dentro de `public_html`, crie uma pasta específica para a ferramenta.

**💡 Nossa sugestão é utilizar o nome `a`.**

É o nome que costumamos utilizar, pois deixa o endereço curto e fácil de acessar.

A estrutura ficará assim:

```text
public_html/
│
├── wp-admin/
├── wp-content/
├── wp-includes/
├── wp-config.php
│
└── a/
    ├── index.php
    ├── conexao.php
    └── update.php
```

O nome `a` é apenas uma sugestão. Você pode escolher outro nome para a pasta.

**Atenção:** usar uma pasta com nome curto não oferece proteção de segurança. Restrinja o acesso à pasta antes de enviar os arquivos.

### 3. Envie os arquivos

Extraia o ZIP baixado do GitHub e envie os três arquivos PHP para dentro da pasta criada:

```text
index.php
conexao.php
update.php
```

Certifique-se de que os arquivos estejam diretamente dentro de `public_html/a/`.

Não é necessário enviar a pasta completa do repositório, o README ou o arquivo de licença para executar a ferramenta.

### 4. Acesse pelo navegador

Com os arquivos no servidor e o acesso devidamente protegido, abra seu navegador.

**Opção 1 — Endereço completo**

```text
https://seudominio.com.br/a/index.php
```

**Opção 2 — Endereço simplificado (recomendado)**

```text
https://seudominio.com.br/a/
```

Como o arquivo principal se chama `index.php`, servidores web configurados para utilizar arquivos de índice normalmente o carregarão automaticamente.

Basta digitar o endereço e pressionar Enter.

### 5. Localize o usuário

Ao acessar a ferramenta, será exibida uma tabela com os usuários cadastrados no WordPress.

A interface apresenta informações como:

- ID do usuário.
- Nome de usuário (login).
- Hash de senha armazenado.
- Endereço de e-mail.
- Opção de edição.

Localize a conta cuja senha deseja redefinir.

### 6. Redefina a senha

Clique no ícone de edição correspondente ao usuário.

Será aberta uma janela para informar uma nova senha.

1. Digite a nova senha.
2. Clique em **Salvar**.
3. Aguarde o retorno à listagem.
4. Teste o acesso ao WordPress com a senha definida.

A versão atual grava a senha utilizando MD5, um mecanismo legado e inadequado para armazenamento seguro de senhas. Recomenda-se atualizar a implementação para utilizar os mecanismos nativos de hash do WordPress antes de disponibilizá-la para uso geral.

### 7. Remova os arquivos após a utilização

**🚨 ETAPA OBRIGATÓRIA DE SEGURANÇA**

Após recuperar o acesso ao WordPress, remova completamente a pasta utilizada.

No nosso exemplo:

```text
public_html/a/
```

Exclua os arquivos:

```text
index.php
conexao.php
update.php
```

Não deixe a ferramenta disponível no servidor.

## 🔒 Segurança e boas práticas

Este projeto foi criado como um utilitário de manutenção e recuperação administrativa.

A implementação atual possui limitações de segurança importantes, incluindo:

- Ausência de autenticação própria.
- Possibilidade de alteração de senhas sem verificação de privilégios na ferramenta.
- Uso de SQL construído diretamente com dados recebidos pelo formulário.
- Exibição de hashes de senha e informações de usuários.
- Utilização de MD5 para redefinição de senhas.

Por isso, **não recomendamos publicar a versão atual em uma URL acessível pela internet sem controles adicionais**.

Para uma implementação mais segura, recomenda-se adicionar autenticação, proteção contra CSRF, consultas parametrizadas, validação de entrada, escape de saída e utilização das APIs nativas do WordPress para alteração de senhas.

O uso deve ocorrer exclusivamente em instalações próprias ou com autorização do responsável, preferencialmente em ambientes locais, isolados ou com acesso restrito.

Nunca compartilhe o endereço temporário de manutenção com pessoas não autorizadas.

## 🛠️ Arquivos do projeto

| Arquivo | Finalidade |
|---|---|
| `index.php` | Interface que lista os usuários e apresenta o formulário de edição. |
| `conexao.php` | Carrega as configurações do WordPress e estabelece a conexão com o banco de dados. |
| `update.php` | Recebe os dados do formulário e executa a alteração da senha no banco de dados. |

O arquivo `conexao.php` espera encontrar o `wp-config.php` um nível acima da pasta da ferramenta. Caso sua estrutura de hospedagem seja diferente, será necessário adaptar esse caminho.

## 🎯 Para quem é indicado?

O projeto pode ser útil para:

- Desenvolvedores WordPress.
- Profissionais de suporte técnico.
- Administradores de hospedagens.
- Agências de criação de sites.
- Profissionais de manutenção e recuperação de acesso.
- Estudantes interessados em entender ferramentas administrativas em PHP.

## 🤝 Contribua com o projeto

Este projeto é open source e está aberto a melhorias da comunidade.

Encontrou algum problema? Tem uma ideia para melhorar o código? Quer contribuir com recursos adicionais ou correções de segurança?

Sua contribuição será bem-vinda!

Você pode:

1. Fazer um Fork do repositório.
2. Criar uma branch para suas alterações.
3. Implementar as melhorias.
4. Enviar um Pull Request.
5. Abrir uma Issue para relatar problemas ou sugerir funcionalidades.

Contribuições que aprimorem a segurança e a compatibilidade com versões recentes do WordPress são especialmente importantes.

## 📄 Licença MIT

Este projeto é disponibilizado sob a **Licença MIT**, permitindo que qualquer pessoa utilize, copie, modifique, distribua e melhore o código, inclusive para fins comerciais.

A licença exige a preservação dos avisos de direitos autorais e do texto da licença nas cópias ou partes substanciais do software.

**Projeto disponibilizado pela CREASY Comunidade.**

Consulte o arquivo [LICENSE](LICENSE) para conhecer os termos completos.

## ⚖️ Isenção de responsabilidade

Este software é fornecido gratuitamente, sem garantias de funcionamento, adequação ou segurança para qualquer finalidade específica, conforme os termos da licença MIT.

Os usuários são responsáveis por garantir que possuem autorização para acessar e modificar os sistemas em que a ferramenta será utilizada.

Recomendamos realizar backup antes de qualquer alteração no banco de dados e utilizar os mecanismos oficiais de recuperação de senha do WordPress sempre que disponíveis.

## 🧡 Sobre a CREASY Comunidade

A **CREASY Comunidade** é um projeto dedicado ao compartilhamento de conhecimento, ferramentas e soluções para desenvolvedores, profissionais de tecnologia, automação, inteligência artificial e marketing digital.

Acreditamos que compartilhar conhecimento e disponibilizar ferramentas open source ajuda a fortalecer a comunidade de tecnologia.

Este repositório é mais uma contribuição para facilitar a rotina de quem trabalha com desenvolvimento e manutenção de sites.

**Repositório oficial:**  
https://github.com/creasycomunidade/recuperar-senha-wordpress

---

### ⭐ Gostou do projeto?

Se esta ferramenta foi útil para você, considere deixar uma estrela no repositório!

Sua contribuição ajuda o projeto a alcançar mais desenvolvedores e profissionais de tecnologia.

**Feito com 🧡 pela CREASY Comunidade.**
