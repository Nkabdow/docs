---
title: Criar um codespace
intro: Você pode criar um codespace para uma branch em um repositório para fazer o desenvolvimento on-line.
product: '{% data reusables.gated-features.codespaces %}'
permissions: '{% data reusables.codespaces.availability %}'
redirect_from:
  - /github/developing-online-with-github-codespaces/creating-a-codespace
  - /github/developing-online-with-codespaces/creating-a-codespace
versions:
  fpt: '*'
  ghec: '*'
type: how_to
topics:
  - Codespaces
  - Fundamentals
  - Developer
shortTitle: Criar um codespace
---

## Sobre a criação do codespace

Você pode criar um codespace em {% data variables.product.prodname_dotcom_the_website %}, em {% data variables.product.prodname_vscode %}, ou usando {% data variables.product.prodname_cli %}. {% data reusables.codespaces.codespaces-are-personal %}

Os codespaces são associados a um branch específico de um repositório e o repositório não pode estar vazio. {% data reusables.codespaces.concurrent-codespace-limit %} Para obter mais informações, consulte "[Excluir um codespace](/github/developing-online-with-codespaces/deleting-a-codespace)".


Ao criar um codespace, várias etapas acontecem para criar e conectar você ao seu ambiente de desenvolvimento:

- Etapa 1: A VM e o armazenamento são atribuídos ao seu codespace.
- Etapa 2: O contêiner é criado e seu repositório é clonado.
- Passo 3: Você pode conectar-se ao codespace.
- Etapa 4: O codespace continua com a configuração pós-criação.

Para obter mais informações sobre o que acontece quando você cria um codespace, consulte "[Aprofundamento](/codespaces/getting-started/deep-dive)".

Para obter mais informações sobre o ciclo de vida de um codespace, consulte "[Ciclo de vida dos codespaces](/codespaces/developing-in-codespaces/codespaces-lifecycle)".

Se você quiser usar hooks do Git para o seu código, você deverá configurar hooks usando os scritps do ciclo de vida do de [`devcontainer.json` lifecycle scripts](https://code.visualstudio.com/docs/remote/devcontainerjson-reference#_lifecycle-scripts), como `postCreateCommand`, durante a etapa 4. Uma vez que o seu contêiner de codespace é criado depois que o repositório é clonado, qualquer [diretório de template do git](https://git-scm.com/docs/git-init#_template_directory) configurado na imagem do contêiner não será aplicado ao seu codespace. Os Hooks devem ser instalados depois que o codespace for criado. Para obter mais informações sobre como usar `postCreateCommand`, consulte a referência [`devcontainer.json` ](https://code.visualstudio.com/docs/remote/devcontainerjson-reference#_devcontainerjson-properties) na documentação do Visual Studio Code.

{% data reusables.codespaces.use-visual-studio-features %}

{% data reusables.codespaces.you-can-see-all-your-codespaces %}

{% data reusables.codespaces.prebuilds-crossreference %}

## Acesso a {% data variables.product.prodname_codespaces %}

{% data reusables.codespaces.availability %}

Quando você tem acesso a {% data variables.product.prodname_codespaces %}, você verá uma aba "Codespace" dentro do menu suspenso ** Código de{% octicon "code" aria-label="The code icon" %} ** ao visualizar um repositório.

Você terá acesso a codespaces nas seguintes condições:

* Você é um integrante de uma organização que habilitou {% data variables.product.prodname_codespaces %} e definiu um limite de gastos.
* Um proprietário da organização concedeu a você acesso a {% data variables.product.prodname_codespaces %}.
* O repositório pertence à organização que habilitou {% data variables.product.prodname_codespaces %}.

{% note %}

**Observação:** As pessoas que já aderiram ao beta com sua conta pessoal do {% data variables.product.prodname_dotcom %} não perderão acesso a {% data variables.product.prodname_codespaces %}. No entanto, {% data variables.product.prodname_codespaces %} para as pessoas, continuará sendo beta.

{% endnote %}

Os proprietários da organização podem permitir que todos os integrantes da organização criem codespaces, limitem a criação de códigos aos integrantes selecionados da organização ou desabilitem a criação de codespace. Para obter mais informações sobre como gerenciar o acesso aos codespaces dentro da sua organização, consulte "[Habilitar codespace para usuários da sua organização](/codespaces/managing-codespaces-for-your-organization/enabling-codespaces-for-your-organization#enable-codespaces-for-users-in-your-organization)".

Antes de {% data variables.product.prodname_codespaces %} pode ser usado em uma organização, um proprietário ou gerente de cobrança deverá ter um limite de gastos. Para obter mais informações, consulte "[Sobre limites de gastos para codespaces](/billing/managing-billing-for-github-codespaces/managing-spending-limits-for-codespaces#about-spending-limits-for-codespaces)".

Se você deseja criar um codespace para um repositório pertencente à sua conta pessoal ou outro usuário e você tem permissão para criar repositórios em uma organização que habilitou {% data variables.product.prodname_codespaces %}, você poderá criar uma bifurcação de repositórios pertencentes ao usuário na organização e, em seguida, criar um codespace para a bifurcação.

## Criar um codespace

{% webui %}

{% data reusables.repositories.navigate-to-repo %}
1. No nome do repositório, use o menu suspenso "Branch", e selecione o branch para o qual você deseja criar um codespace.

   ![Menu suspenso do branch](/assets/images/help/codespaces/branch-drop-down.png)

1. Click the **{% octicon "code" aria-label="The code icon" %} Code** button, then click the **Codespaces** tab.

   ![Botão de codespace novo](/assets/images/help/codespaces/new-codespace-button.png)

1. Create your codespace, either using the default options, or after configuring advanced options:

   * **Use the default options**

      To create a codespace using the default options, click **Create codespace on BRANCH**.

      Optionally, before clicking **Create codespace on BRANCH**, you can click the down arrow at the side of the button to see what machine type will be used for your codespace.

      ![View the default machine type](/assets/images/help/codespaces/default-machine-type.png)

      {% note %}

      **Note**: The machine type with the lowest resources that are valid for the repository is selected by default.

      {% endnote %}

   * **Configure options**

      To configure advanced options for your codespace, such as a different machine type or a particular `devcontainer.json` file:

      1. Click the down arrow at the side of the **Create codespace on BRANCH** button, then click **Configure and create codespace**.
      1. Click the **Configure and create codespace** button.
      1. On the options page for your codespace, choose your preferred options from the drop-down menus.

         ![The codespace options page](/assets/images/help/codespaces/advanced-options.png)

         {% note %}

         **Observações**

         * You can bookmark the options page to give you a quick way to create a codespace for this repository and branch.
         * The [https://github.com/codespaces/new](https://github.com/codespaces/new) page provides a quick way to create a codespace for any repository and branch.
         * For more information about the `devcontainer.json` file, see "[Introduction to dev containers](/codespaces/setting-up-your-project-for-codespaces/introduction-to-dev-containers#devcontainerjson)."
         * For more information about machine types, see "[Changing the machine type for your codespace](/codespaces/customizing-your-codespace/changing-the-machine-type-for-your-codespace#about-machine-types)."
         * {% data reusables.codespaces.codespaces-machine-type-availability %}

         {% endnote %}

      1. Click **Start session**.

{% endwebui %}

{% vscode %}

{% data reusables.codespaces.creating-a-codespace-in-vscode %}

{% endvscode %}

{% cli %}

{% data reusables.cli.cli-learn-more %}

Para criar um novo codespace, use o subcomando `gh create`.

```shell
gh codespace create 
```

Solicita-se que você escolha um repositório, um branch e um tipo de máquina (se mais de um estiver disponível).

{% note %}

**Note**: Currently, {% data variables.product.prodname_cli %} doesn't allow you to choose a dev container configuration when you create a codespace. If you want to choose a specific dev container configuration, use the {% data variables.product.prodname_dotcom %} web interface to create your codespace. For more information, click the "Web browser" tab at the top of this page.

{% endnote %}

Como alternativa, você pode usar sinalizadores para especificar algumas ou todas as opções:

```shell
gh codespace create -r <em>owner</em>/<em>repo</em> -b <em>branch</em> -m <em>machine-type</em> 
```

Substitua `proprietário/repositório` pelo identificador do repositório. Substitua `branch` pelo nome do branch ou o hash SHA completo do commit, que você deseja fazer check-out inicialmente no codespace. Se você usar o sinalizador `-r` sem o sinalizador `b`, o codespace será criado a partir do branch padrão.

Substitua `machine-type` por um identificador válido para um tipo de máquina disponível. Os identificadores são strings como: `basicLinux32gb` e `standardLinux32gb`. The type of machines that are available depends on the repository, your personal account, and your location. Se você digitar um tipo de máquina inválido ou indisponível, os tipos disponíveis serão mostrados na mensagem de erro. Se você omitir este sinalizador e mais de um tipo de máquina estiver disponível, será solicitado que você escolha uma na lista.

Para obter mais informações sobre esse comando, consulte [o manual de{% data variables.product.prodname_cli %}](https://cli.github.com/manual/gh_codespace_create).

{% endcli %}
