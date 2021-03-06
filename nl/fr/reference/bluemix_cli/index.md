---



copyright:

  years: 2015, 2017
lastupdated: "2017-07-12"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Initiation à l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}
{: #getting-started}

L'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} vous permet d'interagir avec vos applications, vos conteneurs et d'autres services via une interface de ligne de commande. 

**Restriction** : l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} n'est pas prise en charge par Cygwin. Ne l'utilisez donc pas dans la fenêtre de ligne de commande Cygwin.

**Remarque** : si votre réseau comporte un serveur proxy HTTP entre l'hôte qui exécute l'interface de ligne de commande et {{site.data.keyword.Bluemix_notm}}, vous devez spécifier le nom d'hôte ou l'adresse IP du serveur proxy dans la variable d'environnement HTTP_PROXY.

**Remarque :** L'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} a intégré une interface de ligne de commande Cloud Foundry dans son installation. Toutefois, il est interdit d'utiliser en même temps des commandes d'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} `bx xxx` et des commandes d'interface de ligne de commande Cloud Foundry `cf xxx` si vous disposez de votre propre installation d'interface de ligne de commande CF. A la place, exécutez `bluemix cf` si vous souhaitez utiliser l'interface de ligne de commande CF pour gérer des ressources Cloud Foundry. En arrière-plan, elle exécute des commandes de l'interface de ligne de commande Cloud Foundry intégrée dans un contexte partagé avec l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}.  De plus, `bluemix cf api/login/logout/target` n'est pas admis, utilisez `bluemix api/login/logout/target` à la place.

## Installation de l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}
{: #install_bluemix_cli}

<!-- Online installation Currently Production Only! Please don't forget to replace the domain name-->

### Installation en ligne

A l'aide d'un accès à une connexion à Internet, copiez et collez la commande suivante dans une console de terminal et exécutez-la.

**macOS**
```
sh <(curl -fsSL https://clis.ng.bluemix.net/install/osx)
```

**Linux**
```
sh <(curl -fsSL https://clis.ng.bluemix.net/install/linux)
```

**Windows PowerShell**

Copiez et collez la commande suivante dans une console de terminal [Windows PowerShell](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/getting-started-with-windows-powershell) et exécutez-la.
```
iex(New-Object Net.WebClient).DownloadString('https://clis.ng.bluemix.net/install/powershell')
```

### Installation hors ligne

<!-- End of online installation -->

Pour Mac OS et Windows, téléchargez le [package de l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}](/docs/cli/index.html#downloads) et exécutez le programme d'installation.

Pour Linux, procédez comme suit :

  1. Téléchargez le package, et décompressez-le. Par exemple :

  ```
  ~$ tar -xvf Bluemix_CLI.tar.gz
  Bluemix_CLI/
  Bluemix_CLI/update_global_config
  Bluemix_CLI/install_bluemix_cli
  Bluemix_CLI/bx/
  Bluemix_CLI/bx/bash_autocomplete
  Bluemix_CLI/bx/zsh_autocomplete
  Bluemix_CLI/bin/
  Bluemix_CLI/bin/bluemix
  ~$
  ```

  2. Accédez au répertoire `Bluemix_CLI`, puis exécutez la commande `./install_bluemix_cli` avec les droits root. Vous pouvez exécuter la commande en tant qu'utilisateur root ou utiliser la commande `sudo` afin d'obtenir les droits root. Par exemple :

  ```
  ~# cd Bluemix_CLI
  ~/Bluemix_CLI# sudo ./install_bluemix_cli
  Superuser privileges are required to run this script.
  The Cloud Foundry CLI version 6.15 is already installed.
  Copying files...
  The Bluemix CLI installed successfully. To get started, open a new Linux terminal and enter "bluemix help", or enter "bx help" as short name.
  ~/Bluemix_CLI#
  ```

Vous pouvez maintenant commencer à utiliser l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} ou installer des plug-in supplémentaires.

## Premières étapes avec l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}

Pour configurer l'outil d'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}, vous devez spécifier l'API à utiliser, qui dépend de la région avec laquelle vous allez travailler (voir ci-dessous la liste des différentes régions) :

```
 ~ $ bluemix regions
Listing Bluemix regions...

Name       Geolocation      Customer   Deployment   Domain               CF API Endpoint                  Type
eu-de      Germany          IBM        Production   eu-de.bluemix.net    https://api.eu-de.bluemix.net    public
au-syd     Sydney           IBM        Production   au-syd.bluemix.net   https://api.au-syd.bluemix.net   public
us-south   US South         IBM        Production   ng.bluemix.net       https://api.ng.bluemix.net       public
eu-gb      United Kingdom   IBM        Production   eu-gb.bluemix.net    https://api.eu-gb.bluemix.net    public
```

Pour la région à laquelle vous voulez accéder, consultez la colonne `CF API Endpoint` et utilisez son contenu pour spécifier le noeud final d'API, comme ci-après :

```
~ $ bluemix api https://api.eu-gb.bluemix.net
Setting api endpoint to https://api.eu-gb.bluemix.net...
OK

API endpoint: https://api.eu-gb.bluemix.net (CF API version: 2.75.0)
Not logged in. Use 'bx login' to log in.
```

Suivez ensuite l'invite pour vous connecter :

```
 ~ $ bluemix login
API endpoint: https://api.eu-gb.bluemix.net

Email> user@example.com

Password>
    Authenticating...
    OK

```

Il est possible de spécifier l'organisation et l'espace à utiliser en vous servant des commutateurs `-o` et `-s`, sinon, la commande login vous invitera à choisir quand plusieurs organisations/espaces seront disponibles.

L'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} est maintenant configurée et prête à être utilisée.

## Installation d'un plug-in
{: #install_plug-in}

L'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} prend en charge une infrastructure d'extension de plug-in permettant d'ajouter des commandes aux commandes intégrées.


Vous pouvez installer un plug-in depuis le référentiel, localement ou à partir d'un serveur distant. {{site.data.keyword.Bluemix_notm}}
possède des référentiels qui hébergent les plug-in de l'interface de ligne de
commande {{site.data.keyword.Bluemix_notm}} et les plug-in de
l'interface de ligne de commande Cloud Foundry :

   * [Référentiel de plug-ins d'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}](http://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins){: new_window} ![External link icon](../../../icons/launch-glyph.svg), qui héberge des plug-ins pour l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}.

Pour procéder à l'installation depuis les référentiels, procédez comme
suit :

  1. Recherchez le plug-in dans le référentiel. Une fois l'interface
de ligne de commande {{site.data.keyword.Bluemix_notm}} installée, le
référentiel officiel `Bluemix` est ajouté par défaut. Vous
pouvez afficher la liste des plug-in du référentiel `Bluemix`
à l'aide de la commande `bluemix plugin repo-plugins`. Par exemple :

  ```
  ~$ bluemix plugin repo-plugins -r Bluemix
  Getting plug-ins from repository 'Bluemix'...

  Repository: Bluemix
  Name           Description                                    Versions
  auto-scaling   Bluemix CLI plugin for Auto-Scaling service    0.2.1, 0.2.2
  nsg            Bluemix Network Security Group plugin          0.1.1

  ~$
  ```

  2. Installez le plug-in depuis le référentiel `Bluemix` à l'aide de la commande `bluemix plugin install`. Par exemple :

  ```
  ~$ bluemix plugin install auto-scaling -r Bluemix
  Looking up 'auto-scaling' from repository 'Bluemix'...
  9857792 bytes downloaded
  Installing plugin '/var/folder/v7/l3hnkz0x0b9b5mf1fyxh7yw00000gn/T/BluemixFileDownload062468676/auto-scaling-darwin-adm64-0.2.2'...
  OK
  Plugin 'auto-scaling 0.2.2' was successfully installed.
  ~$
  ```


Pour installer un plug-in depuis votre environnement local, procédez comme suit :

  1. Téléchargez le plug-in. Par exemple :

  ```
  ~$ wget http://public.dhe.ibm.com/cloud/bluemix/cli/bluemix-plugins/auto-scaling-darwin-amd64.0.2.2--2016-02-18 14:02:12-- http://public.dhe.ibm.com/cloud/bluemix/cli/bluemix-plugins/auto-scaling-darwin-amd64.0.2.2
  Resolving public.dhe.ibm.com... 9.17.248.112
  Connection to public.dhe.ibm.com|9.17.248.112|:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 9857792 (9.4M) [text/plain]
  Saving to: 'auto-scaling-darwin-amd64-0.2.2'

  auto-scaling-darwin-0.2.2 100%[===================>] 9.40M 518KB/s in 22s

  2016-02-18 14:02:34 (443 KB/s) - `auto-scaling-darwin-amd64-0.2.2' saved [9857792/9857792]
  ```

  2. Pour les systèmes similaires à UNIX, vous devez rendre le fichier téléchargé exécutable avec la commande `chmod`. Par exemple :

  ```
  ~$ sudo chmod 755 auto-scaling-darwin-amd64-0.2.2
  Password:
  ~$
  ```

  3. Installez le plug-in à l'aide de la commande `bluemix plugin install`. Par exemple :

  ```
  ~$ bluemix plugin install ./auto-scaling-darwin-amd64-0.2.2
  Installing pluign './auto-scaling-darwin-amd64-0.2.2'...
  OK
  Plugin 'auto-scaling 0.2.2' was successfully installed.
  ~$
  ```

Pour procéder à l'installation depuis un serveur distant,
procédez comme suit :

  1. Installez le plug-in directement depuis une adresse URL
distante à l'aide de la commande `bluemix plugin install`. Par exemple :

  ```
  ~$ bluemix plugin install http://public.dhe.ibm.com/cloud/bluemix/cli/bluemix-plugins/auto-scaling-darwin-amd64-0.2.2
  Attempting to download the binary file...
  9857792 bytes downloaded
  Installing plugin '/var/folder/v7/l3hnkz0x0b9b5mf1fyxh7yw00000gn/T/BluemixFileDownload274645142/auto-scaling-darwin-adm64-0.2.2'...
  OK
  Plugin 'auto-scaling 0.2.2' was successfully installed.
  ~$
  ```


Vous êtes désormais prêt à utiliser les lignes de commande {{site.data.keyword.Bluemix_notm}}. Exécutez `bluemix help` pour afficher la liste de commandes et de descriptions. 

## Contactez-nous

Utilisez les options suivantes pour rechercher des informations sur les éditions, fournir des commentaires et poser des questions :
 * Pour plus d'informations sur les dernières éditions et pour signaler des problèmes : [{{site.data.keyword.Bluemix_notm}} CLI SDK](https://github.com/IBM-Bluemix/bluemix-cli-sdk){: new_window} ![External link icon](../../../icons/launch-glyph.svg)
 * Pour poser des questions et partager vos connaissances avec la communauté : [bluemix-cli Slack channel](https://dwopen.slack.com/messages/bluemix-cli/){: new_window} ![External link icon](../../../icons/launch-glyph.svg)
