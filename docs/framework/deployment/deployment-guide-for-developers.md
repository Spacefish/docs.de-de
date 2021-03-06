---
title: "Handbuch für die Bereitstellung von .NET Framework für Entwickler"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 287005af09f3f022c368d3c8fab12ad02b30e944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="net-framework-deployment-guide-for-developers"></a>Handbuch für die Bereitstellung von .NET Framework für Entwickler
Dieses Thema enthält Informationen für Entwickler, die zu installierenden der [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, das [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2, oder der .NET Framework-4.7 oder 4.7.1 mit ihren apps.

Downloadlinks finden Sie im Abschnitt [Verteilbare Pakete](#redistributable-packages). Sie können die verteilbaren Pakete und Language Packs auch von diesen Microsoft Download Center-Seiten herunterladen:

- .NET Framework 4.7.1 für alle Betriebssysteme ([Webinstaller](http://go.microsoft.com/fwlink/?LinkId=852095) oder [offlineinstaller](http://go.microsoft.com/fwlink/p/?LinkId=852107))

- .NET Framework 4.7 für alle Betriebssysteme ([Webinstaller](http://go.microsoft.com/fwlink/?LinkId=825299) oder [Offlineinstaller](http://go.microsoft.com/fwlink/p/?LinkId=825303))

- [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] für alle Betriebssysteme ([Webinstaller](http://go.microsoft.com/fwlink/?LinkId=780597) oder [Offlineinstaller](http://go.microsoft.com/fwlink/p/?LinkId=780601))

- [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] für alle Betriebssysteme ([Webinstaller](http://go.microsoft.com/fwlink/?LinkId=671729) oder [Offlineinstaller](http://go.microsoft.com/fwlink/p/?LinkId=671744))

- [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] für alle Betriebssysteme ([Webinstaller](http://go.microsoft.com/fwlink/?LinkId=528222) oder [Offlineinstaller](http://go.microsoft.com/fwlink/p/?LinkId=528232))

- .NET Framework 4.5.2 für alle Betriebssysteme ([Webinstaller](http://go.microsoft.com/fwlink/p/?LinkId=397703) oder [Offlineinstaller](http://go.microsoft.com/fwlink/p/?LinkId=397706))

- .NET Framework 4.5.1 für alle Betriebssysteme ([Webinstaller](http://go.microsoft.com/fwlink/p/?LinkId=310158) oder [Offlineinstaller](http://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET Framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)

 Wichtige Hinweise:

> [!NOTE]
> Der Ausdruck "die [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] und dessen Punktversionen" bezieht sich auf die [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] und alle späteren Versionen.

- Die [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 und 4.7.1 sind direkte Updates für die [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], d. h., sie dieselbe Laufzeitversion verwenden, aber die Assemblyversionen werden aktualisiert und enthalten neue Typen und Member.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] und die Punktversionen bauen inkrementell auf [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]auf. Bei der Installation der [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 oder 4.7.1 auf einem System mit der [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] installiert haben, werden die Assemblys der Version 4 durch neuere Versionen ersetzt.

- Wenn Sie in Ihrer App auf ein Microsoft [Out-of-Band-Paket](http://msdn.microsoft.com/library/dn151288\(v=vs.110\).aspx) verweisen, wird die Assembly in das App-Paket aufgenommen.

- Sie müssen über Administratorrechte verfügen, um [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] und die Punktversionen zu installieren.

- Das [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ist in [!INCLUDE[win8](../../../includes/win8-md.md)] und [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]enthalten. Daher müssen Sie für diese Betriebssysteme .NET Framework nicht mit Ihrer App bereitstellen. Entsprechend ist [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] in [!INCLUDE[win81](../../../includes/win81-md.md)] und Windows Server 2012 R2 enthalten. .NET Framework 4.5.2 ist in keinem Betriebssystem enthalten. Das [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ist in Windows 10 enthalten, das [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ist im November-Update von Windows 10 enthalten, und das [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ist im Windows 10 Anniversary Update enthalten.  Der .NET Framework-4.7 in Ersteller-Update für Windows 10 enthalten ist, und .NET Framework 4.7.1 im Herbst-Ersteller-Update für Windows 10 enthalten ist. Eine vollständige Liste der Hardware- und Softwareanforderungen finden Sie unter [Systemanforderungen für .NET Framework](../../../docs/framework/get-started/system-requirements.md).

- Ab [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]können die Benutzer während des Setups eine Liste der aktiven .NET Framework-Apps anzeigen und diese Apps einfach schließen. Dies hilft möglicherweise, durch .NET Framework-Installationen verursachte Systemneustarts zu vermeiden. Informationen hierzu finden Sie unter [Reduzieren von Systemneustarts](../../../docs/framework/deployment/reducing-system-restarts.md).

- Durch das Deinstallieren von [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] oder einer entsprechenden Punktversion werden auch bereits vorhandene [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] -Dateien entfernt. Wenn Sie wieder [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]verwenden möchten, müssen Sie diese Version und alle Updates für sie neu installieren. (Siehe den Artikel zum [Installieren von .NET Framework 4](http://msdn.microsoft.com/library/5a4x27ek\(v=vs.100\).aspx).)

- Die Redistributable-Version von .NET Framework 4.5 wurde am 9. Oktober 2012 aktualisiert, um ein Problem im Zusammenhang mit einem falschen Zeitstempel in einem digitalen Zertifikat zu beheben. Dies verursachte den vorzeitigen Ablauf der digitalen Signatur auf von Microsoft erstellten und signierten Dateien. Wenn Sie zuvor das .NET Framework 4.5 Redistributable Package vom 16. August 2012 installiert hatten, wird empfohlen, die Kopie anhand des neuesten verteilbaren Pakets aus dem [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=245484)zu aktualisieren. Weitere Informationen zu diesem Problem finden Sie in der [Microsoft-Sicherheitsempfehlung (2749655)](http://technet.microsoft.com/security/advisory/2749655).

 Informationen zum Bereitstellen von .NET Framework und den Systemabhängigkeiten in einem Netzwerk durch einen Systemadministrator finden Sie im [Deployment Guide for Administrators (Handbuch für die Bereitstellung für Administratoren)](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Bereitstellungsoptionen für die App
 Wenn Sie die App auf einem Webserver oder an einem anderen zentralen Speicherort veröffentlichen, damit sie von Benutzern installiert werden kann, können Sie aus mehreren Bereitstellungsmethoden auswählen. Einige davon werden mit Visual Studio bereitgestellt. Die folgende Tabelle listet die Bereitstellungsoptionen für Ihre app und gibt das .NET Framework redistributable Package, das jeweilige Option unterstützt. Außerdem können Sie ein benutzerdefiniertes Setupprogramm für die App schreiben. Weitere Informationen finden Sie im Abschnitt [Verketten der .NET Framework-Installation mit dem Setup der App](#chaining).

|Bereitstellungsstrategie für die App|Verfügbare Bereitstellungsmethoden|Zu verwendendes verteilbares .NET Framework-Paket|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Installation aus dem Web|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [WiX-Toolset](#wix)<br />- [Manuelle Installation](#installing_manually)|[Web installer](#redistributable-packages)|
|Installation von Datenträger|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [WiX-Toolset](#wix)<br />- [Manuelle Installation](#installing_manually)|[Offline installer](#redistributable-packages)|
|Installation von einem lokalen Netzwerk (für Unternehmens-Apps)|- [ClickOnce](#clickonce-deployment)|Entweder [Webinstaller](#redistributable-packages) (siehe [ClickOnce](#clickonce-deployment) für Einschränkungen) oder [Offlineinstaller](#redistributable-packages)|

## <a name="redistributable-packages"></a>Verteilbare Pakete
 .NET Framework ist in zwei verteilbaren Paketen verfügbar: Webinstaller (Bootstrapper) und Offlineinstaller (eigenständiges verteilbares Paket). In der folgenden Tabelle werden die beiden Pakettypen verglichen.

||Webinstaller|Offlineinstaller|
|-|-------------------|-----------------------|
|Downloaddatei|.NET Framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](http://go.microsoft.com/fwlin/?LinkId=852092)<br/><br/>.NET Framework 4.7: <br />[NDP47-KB3186500-Web.exe](http://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151802-Web.exe](http://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]:<br />[NDP461-KB3102438-Web.exe](http://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]:<br />[NDP46-KB3045560-Web.exe](http://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](http://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2859818-Web.exe](http://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_setup.exe](http://go.microsoft.com/fwlink/?LinkId=225704)|.NET Framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET Framework 4.7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_x86_x64.exe](http://go.microsoft.com/fwlink/?LinkId=225702)|
|Internetverbindung erforderlich?|Ja|Nein|
|Größe des Downloads|Kleiner (enthält nur Installationsprogramm für die Zielplattform)*|Größer*|
|Language Packs|Enthalten**|Muss [getrennt installiert werden](#chain_langpack), außer Sie verwenden das Paket, das auf alle Betriebssysteme abzielt|
|Bereitstellungsmethode|Unterstützt alle Methoden:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [Manuelle Installation](#installing_manually)<br />- [Benutzerdefiniertes Setup (Verkettung)](#chaining)|Unterstützt alle Methoden:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [Manuelle Installation](#installing_manually)<br />- [Benutzerdefiniertes Setup (Verkettung)](#chaining)|
|Speicherort des Downloads bei ClickOnce-Bereitstellung|Microsoft Download Center:<br /><br /> - [.NET Framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET Framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET Framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET Framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET Framework 4.5.2](http://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET Framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET Framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|Ihr eigener Server oder das Microsoft Download Center:<br /><br /> - [.NET Framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET Framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET Framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET Framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET Framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET Framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET Framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|

 \* Der Offlineinstaller ist das größere Paket, da es Komponenten für alle Zielplattformen enthält. Nach Abschluss des Setups speichert das Windows-Betriebssystem nur das Installationsprogramm, das verwendet wurde. Wenn der Offlineinstaller nach der Installation gelöscht wird, ist die Menge an verwendetem Speicherplatz identisch zum Webinstaller. Wenn Sie das Tool zu verwenden (z. B. [InstallAware](#installaware-deployment) oder [InstallShield](#installshield-deployment)) zum Erstellen des Setupprogramms Ihrer app enthält einen Ordner der Setup-Datei, die nach der Installation entfernt wird, kann der offline-Installers automatisch gelöscht, indem Sie ihn in den Ordner "Setup" platzieren.

 ** Wenn Sie den Webinstaller mit benutzerdefiniertem Setup verwenden, können Sie die Standardspracheinstellungen auf Grundlage der MUI (Multilingual User Interface)-Einstellung des Benutzers verwenden oder in der Befehlszeile mit der `/LCID` -Option ein anderes Language Pack angeben. Entsprechende Beispiele finden Sie im Abschnitt [Verketten mithilfe der .NET Framework-Standardbenutzeroberfläche](#chaining_default) .

## <a name="deployment-methods"></a>Bereitstellungsmethoden
 Vier Bereitstellungsmethoden zur Verfügung stehen:

- Sie können eine Abhängigkeit von .NET Framework festlegen. Sie können mit einer der folgenden Methoden .NET Framework als erforderliche Komponente in der Installation der App angeben:

    - Verwenden der [ClickOnce-Bereitstellung](#clickonce-deployment) (in Visual Studio verfügbar)

    - Erstellen einer [InstallAware Projekt](#installaware-deployment) (kostenlose Edition von Visual Studio-Benutzern)

    - Erstellen eines [InstallShield-Projekts](#installshield-deployment) (in Visual Studio verfügbar)

    - Verwenden des [WiX (Windows Installer XML)-Toolsets](#wix)

- Sie können die Benutzer bitten, [.NET Framework manuell zu installieren](#installing_manually).

- Sie können das Setup von .NET Framework mit dem Setup der App verketten (in das Setup einschließen) und festlegen, wie der .NET Framework-Installationsvorgang erfolgen soll:

    - [Verwenden der Standardbenutzeroberfläche](#chaining_default) Ausführen der Installation durch das .NET Framework-Installationsprogramm

    - [Anpassen der Benutzeroberfläche](#chaining_custom) , um einen einheitlichen Installationsvorgang bereitzustellen und den .NET Framework-Installationsstatus zu überwachen

 Diese Bereitstellungsmethoden werden in den folgenden Abschnitten ausführlich erläutert.

## <a name="setting-a-dependency-on-the-net-framework"></a>Festlegen einer Abhängigkeit von .NET Framework
Wenn Sie ClickOnce, InstallAware, InstallShield oder WiX Bereitstellen Ihrer app verwenden, können Sie eine Abhängigkeit auf .NET Framework hinzufügen, damit sie als Teil der app installiert werden kann.

### <a name="clickonce-deployment"></a>ClickOnce-Bereitstellung
 ClickOnce-Bereitstellung ist für Projekte verfügbar, die mit Visual Basic und Visual C# wurden, ist für Visual C++ jedoch nicht verfügbar.

 So wählen Sie in Visual Studio die ClickOnce-Bereitstellung aus und fügen eine Abhängigkeit von .NET Framework hinzu:

1.  Öffnen Sie das App-Projekt, das Sie veröffentlichen möchten.

2.  Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften**aus.

3.  Wählen Sie den Bereich **Veröffentlichen** aus.

4.  Klicken Sie auf die Schaltfläche **Erforderliche Komponenten** .

5.  Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.

6.  Suchen Sie in der Liste der erforderlichen Komponenten nach der Version von .NET Framework, mit der Sie Ihr Projekt erstellt haben, und wählen Sie diese Version aus.

7.  Wählen Sie eine Option aus, um den Quellspeicherort für die erforderlichen Komponenten anzugeben, und klicken Sie dann auf **OK**.

     Wenn Sie als Downloadspeicherort für .NET Framework eine URL festlegen, können Sie die Microsoft Download Center-Website oder eine eigene Website angeben. Wenn Sie das verteilbare Paket auf einem eigenen Server ablegen, müssen Sie den Offlineinstaller verwenden, nicht den Webinstaller. Sie können lediglich einen Link zum Webinstaller im Microsoft Download Center verwenden. Die URL kann auch auf einen Datenträger verweisen, auf dem eine eigene App verteilt wird.

8.  Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **OK**.

<a name="installaware"></a> 
### <a name="installaware-deployment"></a>InstallAware-Bereitstellung
InstallAware erstellt Windows-app (APPX), Windows Installer (MSI), systemeigenen Code (EXE) und App-V (Application Virtualization)-Paketen aus einer einzigen Quelle. Einfache [enthalten eine Version von .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) im Setup, optional das Anpassen der Installation von [bearbeiten die Standardskripts](https://www.installaware.com/msicode.htm). Beispielsweise vorab InstallAware werden Zertifikate installiert, auf Windows 7, ohne die .NET Framework 4.7 Setup schlägt fehl. Weitere Informationen zu InstallAware, finden Sie unter der [InstallAware für Windows Installer](https://www.installaware.com/) Website.

### <a name="installshield-deployment"></a>InstallShield-Bereitstellung
 So wählen Sie in Visual Studio die InstallShield-Bereitstellung aus und fügen eine Abhängigkeit von .NET Framework hinzu

1.  Wählen Sie auf der Visual Studio-Menüleiste **Datei**, **Neu**und **Projekt**aus.

2.  Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** nacheinander **Andere Projekttypen**, **Setup und Bereitstellung**und **InstallShield LE**aus.

3.  Geben Sie im Feld **Name** einen Namen für das Projekt ein, und klicken Sie dann auf **OK**.

4.  Wenn Sie ein Projekt für Setup und Bereitstellung zum ersten Mal erstellen, wählen Sie **zu InstallShield wechseln** oder **InstallShield Limited Edition aktivieren** zum Herunterladen von InstallShield Limited Edition für Ihre Version von Microsoft Visual Studio. Starten Sie Visual Studio neu.

5.  Wechseln Sie zum **Projekt-Assistenten** , und wählen Sie **Anwendungsdateien** aus, um die Projektausgabe hinzuzufügen. Sie können mit diesem Assistenten weitere Projektattribute konfigurieren.

6.  Wechseln Sie zu **Installationsanforderungen** , und wählen Sie die Betriebssysteme und die Version von .NET Framework aus, die Sie installieren möchten.

7.  Öffnen Sie das Kontextmenü für das Setup-Projekt, und wählen Sie **Erstellen**aus.
 
<a name="wix"></a> 
### <a name="windows-installer-xml-wix-deployment"></a>WiX (Windows Installer XML)-Bereitstellung
 Mit dem WiX (Windows Installer XML)-Toolset werden Windows-Installationspakete aus XML-Quellcode erstellt. WiX unterstützt eine Befehlszeilenumgebung, die in die Buildprozesse integriert werden kann, um MSI- und MSM-Setuppakete zu erstellen. Mit WiX können Sie [.NET Framework als erforderliche Komponente angeben](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), oder Sie können [einen Chainer erstellen](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) , um die Bereitstellung von .NET Framework vollständig zu steuern. Weitere Informationen zu WiX finden Sie auf der Website für das [WiX (Windows Installer XML)-Toolset](http://wixtoolset.org/) .

<a name="installing_manually"></a> 
## <a name="installing-the-net-framework-manually"></a>Manuelles Installieren von .NET Framework
 In manchen Situationen kann die automatische Installation von .NET Framework mit Ihrer Anwendung möglicherweise nicht ausgeführt werden. In diesem Fall können Sie .NET Framework von den Benutzern selbst installieren lassen. Das verteilbare Paket ist in [zwei Paketen](#redistributable-packages)verfügbar. Im Setupprozess stellen Sie Anweisungen dafür bereit, wie Benutzer zur Suche und Installation von .NET Framework vorgehen müssen.

<a name="chaining"></a> 
## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Verketten der .NET Framework-Installation mit dem Setup der App
 Wenn Sie ein benutzerdefiniertes Setupprogramm für die App erstellen, können Sie den .NET Framework-Setupvorgang mit dem Setupvorgang der App verketten (in das Setup einschließen). Durch das Verketten werden zwei Benutzeroberflächenoptionen für die .NET Framework-Installation bereitgestellt:

- Verwenden der vom .NET Framework-Installationsprogramm bereitgestellten Standardbenutzeroberfläche

- Erstellen einer benutzerdefinierten Benutzeroberfläche für die .NET Framework-Installation, die mit dem Setupprogramm der App konsistent ist

 Beide Methoden ermöglichen es Ihnen, entweder den Webinstaller oder den Offlineinstaller zu verwenden. Jedes Paket bietet eigene Vorteile:

- Beim Verwenden des Webinstallers erkennt das .NET Framework-Setup, welches Installationspaket erforderlich ist, und lädt nur dieses Paket herunter und installiert es.

- Beim Verwenden des Offlineinstallers können Sie den vollständigen Satz von .NET Framework-Installationspaketen in die Verteilungsmedien einschließen, damit die Benutzer während des Setups keine zusätzlichen Dateien aus dem Web herunterladen müssen.

<a name="chaining_default"></a> 
### <a name="chaining-by-using-the-default-net-framework-ui"></a>Verketten mithilfe der .NET Framework-Standardbenutzeroberfläche
 Zum automatischen Verketten des .NET Framework-Installationsvorgangs und Bereitstellen der Benutzeroberfläche durch das .NET Framework-Installationsprogramm fügen Sie dem Setupprogramm den folgenden Befehl hinzu:

```
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>
```

 Wenn beispielsweise das Programm "Contoso.exe" lautet und Sie das eigenständige verteilbare [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] -Offlinepaket automatisch installieren lassen möchten, verwenden Sie folgenden Befehl:

```
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso
```

 Sie können die Installation mit zusätzlichen Befehlszeilenoptionen anpassen. Beispiel:

- Um Benutzern das Schließen aktiver .NET Framework-Apps zu ermöglichen und Systemneustarts zu minimieren, legen Sie den passiven Modus fest, und verwenden Sie die Option `/showrmui` wie folgt:

    ```
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso
    ```

     Dieser Befehl ermöglicht dem Neustart-Manager das Anzeigen eines Meldungsfelds, das Benutzern die Möglichkeit bietet, .NET Framework-Apps zu schließen, bevor das .NET Framework installiert wird.

- Wenn Sie den Webinstaller verwenden, können Sie mit der Option `/LCID` ein Language Pack angeben. Um beispielsweise den [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] -Webinstaller mit dem Contoso-Setupprogramm zu verketten und das Language Pack "Japanisch" zu installieren, fügen Sie dem Setupvorgang der App den folgenden Befehl hinzu:

    ```
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041
    ```

     Wenn Sie die Option `/LCID` weglassen, wird das Language Pack installiert, das der Benutzereinstellung für die MUI entspricht.

    > [!NOTE]
    > Unterschiedliche Language Packs können verschiedene Versionsdatumsangaben aufweisen. Wenn das angegebene Language Pack im Download Center nicht verfügbar ist, wird .NET Framework ohne das Language Pack installiert. Wenn .NET Framework auf dem Computer des Benutzers bereits installiert ist, wird nur das Language Pack installiert.

 Eine vollständige Liste der Optionen finden Sie im Abschnitt [Befehlszeilenoptionen](#command-line-options) .

 Häufige Rückgabecodes finden Sie im Abschnitt [Rückgabecodes](#return-codes) .

<a name="chaining_custom"></a>
### <a name="chaining-by-using-a-custom-ui"></a>Verketten mithilfe einer benutzerdefinierten Benutzeroberfläche
 Wenn Sie ein benutzerdefiniertes Setuppaket verwenden, können Sie das .NET Framework-Setup automatisch starten und eine eigene Ansicht des Setupstatus anzeigen lassen. Stellen Sie in diesem Fall sicher, dass der Code folgenden Anforderungen entspricht:

- Überprüfung auf [Hardware- und Softwareanforderungen für .NET Framework](../../../docs/framework/get-started/system-requirements.md).

- [Erkennen](#detect_net) , ob bereits die richtige Version von .NET Framework auf dem Computer des Benutzers installiert ist.

    > [!IMPORTANT]
    > Bei der Bestimmung, ob die richtige Version von .NET Framework bereits installiert ist, sollten Sie überprüfen, ob Ihre Zielversion *oder* eine höhere Version installiert ist und nicht nur, ob Ihre Zielversion installiert ist. Sie sollen also bewerten, ob der Release-Schlüssel, den Sie aus der Registrierung enthalten, größer oder gleich dem Release-Schlüssel Ihrer Zielversion ist und *nicht* , ob er gleich dem Release-Schlüssel Ihrer Zielversion ist.

- [Erkennen](#detecting-the-language-packs) , ob die Language Packs bereits auf dem Computer des Benutzers installiert sind.

- Wenn Sie die Bereitstellung steuern möchten, lassen Sie den .NET Framework-Setupvorgang automatisch starten und nachverfolgen (weitere Informationen finden Sie unter [How to: Get Progress from the .NET Framework 4.5 Installer](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)).

- Wenn Sie den Offlineinstaller bereitstellen, [verketten Sie die Language Packs separat](#chain_langpack).

- Passen Sie die Bereitstellung mit [Befehlszeilenoptionen](#command-line-options)an. Wenn Sie beispielsweise den .NET Framework-Webinstaller verketten, jedoch das standardmäßige Language Pack überschreiben möchten, verwenden Sie die `/LCID` -Option, wie im vorherigen Abschnitt beschrieben.

- [Problembehandlung](#troubleshooting).

<a name="detect_net"></a>
### <a name="detecting-the-net-framework"></a>Erkennen von .NET Framework
 Das .NET Framework-Installationsprogramm schreibt Registrierungsschlüssel, wenn die Installation erfolgreich verläuft. Sie können testen, ob das [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] oder höher durch die Überprüfung des `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`-Ordners in der Registrierung für einen `DWORD`-Wert namens `Release` installiert wird. (Beachten Sie, dass „.NET Framework Setup“ nicht mit einem Punkt beginnt.) Wenn dieser Schlüssel vorhanden ist, bedeutet dies, dass [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] oder eine höhere Version auf dem Computer installiert wurde. Der Wert von `Release` gibt an, welche Version von .NET Framework installiert ist.

> [!IMPORTANT]
> Beim Versuch zu das Vorhandensein einer bestimmten Version zu ermitteln, sollten Sie prüfen, ob ein Wert vorhanden ist, der  **größer als oder gleich** dem Wert des Releaseschlüsselworts ist.

|Version|Wert des Versions-DWORD|
|-------------|--------------------------------|
|.NET Framework auf Windows 10 fallen Ersteller Update installiert 4.7.1|461308|
|.NET Framework installiert auf allen Betriebssystemen außer Windows 10 fallen Ersteller Update 4.7.1|461310|
|.NET Framework 4.7 installiert unter Windows 10 Creators Update|460798|
|.NET Framework 4.7 wird unter allen Betriebssystemen außer Windows 10 Creators Update installiert|460805|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] installiert auf der Windows 10 Anniversary Edition|394802|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] installiert auf allen Betriebssystemen außer der Windows 10 Anniversary Edition|394806|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] installiert unter Windows 10, Update von November|394254|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] installiert unter allen Betriebssystemen außer Windows 10, Update von November|394271|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] installiert unter Windows 10|393295|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] installiert auf allen anderen Windows 10-Betriebssystemversionen|393297|
|.NET Framework 4.5.2|379893|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] installiert mit [!INCLUDE[win81](../../../includes/win81-md.md)] oder Windows Server 2012 R2|378675|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] installiert unter [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|378389|

### <a name="detecting-the-language-packs"></a>Erkennen der Sprachpakete
 Sie können testen, ob ein bestimmtes Sprachpaket installiert ist, indem Sie in der Registrierung überprüfen, ob der Ordner „HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID*“ den DWORD-Wert mit dem Namen `Release` enthält. (Beachten Sie, dass „.NET Framework Setup“ nicht mit einem Punkt beginnt.) *LCID* gibt einen Gebietsschemabezeichner an. Eine Liste dieser Bezeichner finden Sie unter [Unterstützte Sprachen](#supported-languages).

 Um z. B. zu ermitteln, ob das vollständige Sprachpaket Japanisch (LCID=1041) installiert ist, suchen Sie in der Registrierung die folgenden Werte:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041
Name: Release
Type: DWORD
```

 Um festzustellen, ob das endgültige Release eines Language Packs, für installiert ist die [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 oder 4.7.1, überprüfen Sie den Wert des RELEASE-Schlüssels DWORD-Wert, die im vorherigen Abschnitt beschriebenen [Erkennen von .NET Framework](#detect_net).

<a name="chain_langpack"></a> 
### <a name="chaining-the-language-packs-to-your-app-setup"></a>Verketten der Sprachpakete mit dem App-Setup
 .NET Framework stellt einen Satz eigenständiger ausführbarer Language Pack-Dateien bereit, die lokalisierte Ressourcen für bestimmte Kulturen enthalten. Die Sprachpakete sind im Microsoft Download Center verfügbar:

- [.NET Framework 4.7.1 Sprachpakete](http://go.microsoft.com/fwlink/p/?LinkId=852090)

- [.NET Framework 4.7 Language Packs](http://go.microsoft.com/fwlink/p/?LinkId=825306)

- [.NET Framework 4.6.2 Language Packs](http://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET Framework 4.6.1 Language Packs](http://go.microsoft.com/fwlink/p/?LinkId=671747)

- [.NET Framework 4.6 Language Packs](http://go.microsoft.com/fwlink/p/?LinkId=528314)

- [.NET Framework 4.5.2 Language Packs](http://go.microsoft.com/fwlink/p/?LinkId=397701)

- [.NET Framework 4.5.1 Language Packs](http://go.microsoft.com/fwlink/p/?LinkId=322101)

- [.NET Framework 4.5-Language Packs](http://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Die Sprachpakete enthalten nicht die zum Ausführen einer App erforderlichen .NET Framework-Komponenten, Sie müssen das .NET Framework mit dem Web- oder Offlineinstaller installieren, bevor Sie ein Sprachpaket installieren.

 Ab [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] haben die Paketnamen das Format „NDP<`version`>-KB<`number`>-x86-x64-AllOS-<`culture`>.exe“, wobei `version` die Versionsnummer von .NET Framework ist, `number` die Nummer eines Artikels in der Microsoft Knowledge Base und `culture` steht für [Land/Region](#supported-languages). Ein Beispiel für einen solchen Paketnamen ist `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Paketnamen sind im Abschnitt [Redistributable Packages](#redistributable-packages) dieses Artikels aufgelistet.

 Um ein Sprachpaket mit dem .NET Framework-Offlineinstaller zu installieren, müssen Sie es mit dem Setup der App verketten. Verwenden Sie beispielsweise zum Bereitstellen des [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] -Offlineinstallers mit dem Language Pack "Japanisch" den folgenden Befehl:

```
NDP451-KB2858728-x86-x64-AllOS-JPN.exe/q /norestart /ChainingPackage <ProductName>
```

 Sie müssen die Language Packs nicht verketten, wenn Sie den Webinstaller verwenden. In diesem Fall installiert Setup das Language Pack, das der MUI-Einstellung des Benutzers entspricht. Wenn Sie eine andere Sprache installieren möchten, können Sie mit der Option `/LCID` ein Language Pack angeben.

 Eine vollständige Liste der Befehlszeilenoptionen finden Sie im Abschnitt [Befehlszeilenoptionen](#command-line-options) .

### <a name="troubleshooting"></a>Problembehandlung

#### <a name="return-codes"></a>Rückgabecodes
 In der folgenden Tabelle sind die häufigsten Rückgabecodes für das verteilbare Installationsprogramm für .NET Framework aufgeführt. Die Rückgabecodes sind für alle Versionen des Installationsprogramms identisch. Links zu ausführlichen Informationen finden Sie im nächsten Abschnitt.

|Rückgabecode|Beschreibung|
|-----------------|-----------------|
|0|Die Installation wurde erfolgreich abgeschlossen.|
|1602|Der Benutzer hat die Installation abgebrochen.|
|1603|Während der Installation ist ein schwerwiegender Fehler aufgetreten.|
|1641|Ein Neustart ist erforderlich, um die Installation abzuschließen. Diese Meldung zeigt eine erfolgreiche Installation an.|
|3010|Ein Neustart ist erforderlich, um die Installation abzuschließen. Diese Meldung zeigt eine erfolgreiche Installation an.|
|5100|Der Computer des Benutzers erfüllt die Systemanforderungen nicht.|

#### <a name="download-error-codes"></a>Downloadfehlercodes
 Finden Sie unter den folgenden Inhalt:

- [Fehlercodes für BITS (Background Intelligent Transfer Service)](http://go.microsoft.com/fwlink/?LinkId=180946)

- [Fehlercodes für URL-Moniker](http://go.microsoft.com/fwlink/?LinkId=180947)

- [Fehlercodes für WinHttp](http://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Sonstige Fehlercodes
 Finden Sie unter den folgenden Inhalt:

- [Fehlercodes für Windows Installer](http://go.microsoft.com/fwlink/?LinkId=180949)

- [Ergebniscodes für Windows Update Agent](http://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Deinstallieren von .NET Framework
 Beginnend mit [!INCLUDE[win8](../../../includes/win8-md.md)], deinstallieren Sie die [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 oder 4.7.1 mit **Windows-Funktionen ein- oder ausschalten** in der Systemsteuerung. In früheren Versionen von Windows, deinstallieren Sie die [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 oder 4.7.1 mit **Software** in der Systemsteuerung.

> [!IMPORTANT]
> Für Windows 7 und ältere Betriebssysteme, deinstallieren die [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 oder 4.7.1 nicht wiederhergestellt werden [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Dateien, und Deinstallieren der [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nicht wiederherstellen [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Dateien. Wenn Sie wieder die ältere Version verwenden möchten, müssen Sie diese Version und alle Updates für sie neu installieren.

## <a name="appendix"></a>Anhang

### <a name="command-line-options"></a>Befehlszeilenoptionen
 In der folgenden Tabelle sind die Optionen aufgeführt, die Sie einschließen können, wenn Sie das verteilbare [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] -Paket mit dem Setup der App verketten.

|Option|Beschreibung|
|------------|-----------------|
|**/CEIPConsent**|Überschreibt das Standardverhalten und sendet anonymes Feedback an Microsoft, um die Bereitstellungsumgebung für die Zukunft zu verbessern. Diese Option kann nur verwendet werden, wenn vom Setupprogramm die Zustimmung angefordert wird und der Benutzer die Berechtigung erteilt, anonymes Feedback an Microsoft zu senden.|
|**/chainingpackage** `packageName`|Gibt den Namen der ausführbaren Datei an, die das Verketten ausführt. Diese Informationen werden als anonymes Feedback an Microsoft gesendet, um zu helfen, die Bereitstellungsumgebung für die Zukunft zu verbessern.<br /><br /> Wenn der Paketname Leerzeichen enthält, verwenden Sie als Trennzeichen doppelte Anführungszeichen, z.B. **/chainingpackage "Lucerne Publishing"**. Ein Beispiel für ein Verkettungspaket finden Sie in der MSDN Library unter [Abrufen von Statusinformationen aus einem Installationspaket](http://go.microsoft.com/fwlink/?LinkId=181926) .|
|**/LCID**  `LCID`<br /><br /> wobei `LCID` einen Gebietsschemabezeichner angibt (siehe [Unterstützte Sprachen](#supported-languages))|Installiert das von `LCID` angegebene Language Pack und erzwingt die Anzeige der Benutzeroberfläche in dieser Sprache (sofern nicht der stille Modus festgelegt wird).<br /><br /> Bei Verwendung des Webinstallers wird mit dieser Option das Language Pack per Verkettung aus dem Web installiert. **Hinweis**: Verwenden Sie diese Option nur mit dem Webinstaller.|
|**/log** `file` &#124; `folder`|Gibt den Speicherort der Protokolldatei an. Der Standardwert ist der temporäre Ordner für den Vorgang, und der Standarddateiname basiert auf dem Paket. Wenn die Dateierweiterung TXT lautet, wird ein Textprotokoll präsentiert. Wenn Sie eine andere Erweiterung oder keine Erweiterung angeben, wird ein HTML-Protokoll erstellt.|
|**/msioptions**|Gibt Optionen an, die für MSI- und MSP-Elemente übergeben werden sollen. Beispiel: `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Verhindert, dass das Setupprogramm automatisch erneut gestartet wird. Wenn Sie diese Option verwenden, muss die verkettende App den Rückgabecode erfassen und den Neustart initiieren (siehe [Abrufen von Statusinformationen aus einem Installationspaket](http://go.microsoft.com/fwlink/?LinkId=179606) in der MSDN Library).|
|**/passive**|Legt den passiven Modus fest. Zeigt die Statusleiste an, um anzugeben, dass die Installation ausgeführt wird, zeigt dem Benutzer jedoch keine Eingabeaufforderungen oder Fehlermeldungen an. In diesem Modus muss, sofern er durch ein Setupprogramm verkettet ist, das Verkettungspaket [Rückgabecodes](#return-codes)behandeln.|
|**/pipe**|Erstellt einen Kommunikationskanal, damit ein Verkettungspaket bearbeitet werden kann.|
|**/promptrestart**|Wenn im passiven Modus das Setupprogramm einen Neustart erfordert, wird der Benutzer zur Eingabe aufgefordert. Bei dieser Option muss der Benutzer eingreifen, wenn ein Neustart erforderlich ist.|
|**/q**|Legt den stillen Modus fest.|
|**/repair**|Löst die Reparaturfunktionalität aus.|
|**/serialdownload**|Erzwingt, dass die Installation erst erfolgt, nachdem das Paket heruntergeladen wurde.|
|**/showfinalerror**|Legt den passiven Modus fest. Zeigt Fehler nur an, wenn die Installation nicht erfolgreich ist. Bei dieser Option muss der Benutzer eingreifen, wenn die Installation nicht erfolgreich ist.|
|**/showrmui**|Wird ausschließlich mit der Option **/passive** verwendet. Zeigt ein Meldungsfeld an, das Benutzer auffordert, derzeit ausgeführte .NET Framework-Apps zu schließen. Dieses Meldungsfeld verhält sich im passiven und im nicht passiven Modus gleich.|
|**/uninstall**|Deinstalliert das verteilbare .NET Framework-Paket.|

### <a name="supported-languages"></a>Unterstützte Sprachen
In der folgenden Tabelle sind die .NET Framework Sprachpakete aufgeführt, die für [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] und die zugehörigen Punktversionen verfügbar sind.

|LCID|Sprache – Land/Region|culture|
|----------|--------------------------------|-------------|
|1025|Arabisch - Saudi-Arabien|ar|
|1028|Chinesisch (traditionell)|zh-Hant|
|1029|Tschechisch|cs|
|1030|Dänisch|da|
|1031|Deutsch (Deutschland)|de|
|1032|Griechisch|el|
|1035|Finnisch|fi|
|1036|Französisch (Frankreich)|fr|
|1037|Hebräisch|er|
|1038|Ungarisch|hu|
|1040|Italienisch (Italien)|it|
|1041|Japanisch|ja|
|1042|Koreanisch|ko|
|1043|Niederländisch (Niederlande)|nl|
|1044|Norwegisch (Bokmål)|Nein|
|1045|Polnisch|pl|
|1046|Portugiesisch (Brasilien)|pt-BR|
|1049|Russisch|ru|
|1053|Schwedisch|sv|
|1055|Türkisch|tr|
|2052|Chinesisch (vereinfacht)|zh-Hans|
|2070|Portugiesisch (Portugal)|pt-PT|
|3082|Spanisch – Spanien (Moderne Sortierreihenfolge)|es|

## <a name="see-also"></a>Siehe auch
 [Bereitstellungshandbuch für Administratoren](../../../docs/framework/deployment/guide-for-administrators.md)  
 [Systemanforderungen](../../../docs/framework/get-started/system-requirements.md)  
 [Installieren Sie .NET Framework für Entwickler](../../../docs/framework/install/guide-for-developers.md)  
 [Problembehandlung bei blockierten Installationen und Deinstallationen von .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
 [Reduzieren von Systemneustarts bei .NET Framework 4.5-Installationen](../../../docs/framework/deployment/reducing-system-restarts.md)  
 [Gewusst wie: Abrufen des Status vom Installationsprogramm für .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
