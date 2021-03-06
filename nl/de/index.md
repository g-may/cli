---



copyright:

  years: 2015, 2017

lastupdated: "2017-06-30"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Manuelle Installation der Befehlszeilenschnittstelle
{: #cli}

Die {{site.data.keyword.Bluemix}}-CLI stellt eine Befehlszeilenbedienung zur Verwaltung Ihrer {{site.data.keyword.Bluemix_notm}}-Umgebung bereit. Sie enthält außerdem eine Cloud Foundry-Befehlszeilenschnittstelle (cf) in ihrer Installation, die zur Verwaltung von Cloud Foundry-Anwendungen und -Services verwendet werden kann.
{:shortdesc}

Beide CLI-Tools verwenden standardmäßig den Port 443. Wenn sich ein HTTP-Proxy zwischen den CLI-Tools und der {{site.data.keyword.Bluemix_notm}}-Umgebung befindet, müssen Sie die Umgebungsvariable `HTTP_PROXY` mit der tatsächlichen URL und dem Port (falls vorhanden) des HTTP-Proxys konfigurieren. Details hierzu finden Sie in den Informationen zur [Verwendung der CLI mit einem HTTP-Proxy-Server ![Symbol für externen Link](../icons/launch-glyph.svg)](http://docs.cloudfoundry.org/cf-cli/http-proxy.html){: new_window}.

[Download der {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle](/docs/cli/reference/bluemix_cli/all_versions.html){: new_window} 

Wenn Sie unter macOS arbeiten, verwenden Sie am besten [IBM Cloud Application Tools 2](/docs/cli/icat.html) für Ihren Einstieg in die Verwendung der IBM Cloud-Tools.
{: tip}

## ![](./images/CLI_Plugin.svg) Befehlszeilenschnittstelle-Plug-ins
{: #cliplugins notoc}

Sie können die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle ohne großen Aufwand durch zusätzliche Befehle erweitern. Zugriff auf die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstellen-Plug-ins erhalten Sie über das [Plug-in-Repository für die Bluemix CLI ![Symbol für externen Link](../icons/launch-glyph.svg)](https://plugins.ng.bluemix.net/){: new_window}.

### Erweitern Sie die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle: bx
{: #cli_bluemix_ext notoc}


Wenn Sie das {{site.data.keyword.Bluemix_notm}}-CLI-Tool installieren, wird das [CLI-Plug-in-Repository ![Symbol für externen Link](../icons/launch-glyph.svg)](https://plugins.ng.bluemix.net/){: new_window} standardmäßig mit dem Repository-Aliasnamen `Bluemix` vorkonfiguriert. Sie können verfügbare Plug-ins direkt installieren.

```
bluemix plugin install Plug-in-Name -r Bluemix
```

| *{{site.data.keyword.autoscaling}}-CLI* |  *IBM Bluemix Container Service*  |
|-----|-----|
| Plug-in-Name: auto-scaling <br> [Dokumentation anzeigen](/docs/cli/plugins/auto-scaling/index.html) |  Plug-in-Name: container-service  <br> [Dokumentation anzeigen](/docs/containers/cs_cli_devtools.html) |
{: caption="Tabelle 2. Plug-ins" caption-side="top"}

|  *Privates Netzpeering* | *Schematics* | *VPN*  |
|-----|-----|-----|
| Plug-in-Name: private-network-peering  <br> [Dokumentation anzeigen](/docs/cli/plugins/pnp/index.html) | Plug-in-Name: Schematics  <br> [Dokumentation anzeigen](/docs/services/schematics/schematics_reference.html) | Plug-in-Name: VPN  <br> [Dokumentation anzeigen](/docs/cli/plugins/bx_vpn/index.html) |
{: caption="Tabelle 3. Plug-ins" caption-side="top"}

Sie können außerdem Plug-ins aus anderen Repositorys hinzufügen, die mit der {{site.data.keyword.Bluemix_notm}}-CLI-Architektur konform sind.
1. Zum Installieren von {{site.data.keyword.Bluemix_notm}}-CLI-Plug-ins aus einem anderen Repository legen Sie den Plug-in-Registry-Endpunkt fest:
```
bluemix plugin repo-add bluemix-other-repo [repo_url]
```
Dabei ist `repo_url` die HTTPS-URL des Plug-in-Repositorys.

2. Führen Sie den folgenden Befehl aus, um ein Plug-in zu installieren:
```
bluemix plugin install Plug-in-Name -r bluemix-other-repo
```

### Erweitern Sie die Cloud Foundry-Befehlszeilenschnittstelle: bx cf
{: #cli_cf_ext notoc}

Nach der Installation der {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle ist auch eine Cloud Foundry-Befehlszeilenschnittstelle im {{site.data.keyword.Bluemix_notm}}-CLI-Verzeichnis installiert. Führen Sie die Cloud Foundry-CLI-Befehle mit `bluemix cf` aus.

* Zum Installieren von CLI-Plug-ins über die {{site.data.keyword.Bluemix_notm}}-Registry müssen Sie den Plug-in-Registry-Endpunkt festlegen:

```
bluemix cf add-plugin-repo bluemix-cf-repo https://plugins.ng.bluemix.net
```
{: codeblock}

* Anschließend führen Sie den folgenden Befehl aus, um ein Plug-in zu installieren:

```
bluemix cf install-plugin Plug-in-Name -r bluemix-cf-repo
```
{: codeblock}

| *Administrationskonsole* | *VPN* |
|-----------------|-----------------|
|  Plug-in-Name: bluemix-admin <br> [Dokumentation anzeigen](/docs/cli/plugins/bluemix_admin/index.html) | Plug-in-Name: VPN <br> [Dokumentation anzeigen](/docs/cli/plugins/vpn/index.html) |
{: caption="Tabelle 4. Plug-ins" caption-side="top"}


## ![](./images/Integrated_Dev_Tools.svg) Integrierte Entwicklungstools
{: #ide notoc}

Sie können Plug-ins herunterladen und installieren, um Ihre bevorzugten {{site.data.keyword.Bluemix_notm}}-Services zu integrieren.

| *Liberty for Java* | *MobileFirst* | *{{site.data.keyword.rules_short}}* | *API Connect* | *Eclipse Tools for Bluemix* |
|----------|----------|----------|----------|----------|
| [Eclipse-Plug-in Liberty ![Symbol für externen Link](../icons/launch-glyph.svg)](https://developer.ibm.com/wasdev/downloads/liberty-profile-using-eclipse/){: new_window} | [Eclipse-Plug-in ![Symbol für externen Link](../icons/launch-glyph.svg)](https://marketplace.eclipse.org/content/ibm-mobilefirst-platform-studio){: new_window} | [Rules Designer Eclipse Plug-in](../services/rules/index.html#rulov002) | [Developer Toolkit](/docs/services/apiconnect/creating_apis.html#install_dev_tk ) | [Bluemix Eclipse Plug-in](/docs/manageapps/eclipsetools/eclipsetools.html) |
{: caption="Tabelle 5. Plug-ins" caption-side="top"}
