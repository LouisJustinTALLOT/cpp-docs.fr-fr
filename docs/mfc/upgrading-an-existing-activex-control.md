---
title: Mise à niveau d'un contrôle ActiveX
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
ms.openlocfilehash: 802640d5132c28dbda564afcb63c12d8a4133042
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353545"
---
# <a name="upgrading-an-existing-activex-control"></a>Mise à niveau d'un contrôle ActiveX

Les contrôles ActiveX existants (anciennement les contrôles OLE) peuvent être utilisés sur Internet sans modification. Toutefois, vous pouvez modifier les contrôles pour améliorer leurs performances.

> [!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Lorsque vous utilisez votre contrôle sur une page Web, il y a d’autres considérations. Le fichier .ocx et tous les fichiers de support doivent être sur la machine cible ou être téléchargés sur Internet. Cela rend la taille du code et le temps de téléchargement une considération importante. Les téléchargements peuvent être emballés dans un fichier .cab signé. Vous pouvez marquer votre contrôle comme sûr pour le script, et comme sûr pour l’initialisation.

Cet article aborde les thèmes suivants :

- [Code d’emballage pour le téléchargement](#_core_packaging_code_for_downloading)

- [Marquage d’un contrôle sûr pour le script et l’initialisation](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [À propos des licences](#_core_licensing_issues)

- [Code de signature](#_core_signing_code)

- [Gestion de la palette](#_core_managing_the_palette)

- [Niveaux de sécurité et contrôle du navigateur Internet Explorer](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Vous pouvez également ajouter des optimisations, telles que décrites dans [ActiveX Controls: Optimization](../mfc/mfc-activex-controls-optimization.md). Les monikers peuvent être utilisés pour télécharger des propriétés et de grandes BLOB asynchronement, comme décrit dans [ActiveX Controls sur Internet](../mfc/activex-controls-on-the-internet.md).

## <a name="packaging-code-for-downloading"></a><a name="_core_packaging_code_for_downloading"></a>Code d’emballage pour le téléchargement

Pour plus d’informations sur ce sujet, voir [Packaging ActiveX Controls](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>L’étiquette CODEBASE

Les contrôles ActiveX sont intégrés dans les pages Web à l’aide de l’étiquette. `<OBJECT>` Le `CODEBASE` paramètre `<OBJECT>` de l’étiquette spécifie l’emplacement à partir duquel télécharger le contrôle. `CODEBASE`peut pointer vers un certain nombre de types de fichiers différents avec succès.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Utilisation de l’étiquette CODEBASE avec un fichier OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Cette solution ne télécharge que le fichier .ocx du contrôle, et nécessite tout DLLs de soutien pour être déjà installé sur la machine cliente. Cela fonctionnera pour les contrôles Internet Explorer et MFC ActiveX construits avec Visual C, parce qu’Internet Explorer expédie avec les DL De support pour les commandes Visual CMD. Si un autre navigateur Internet capable de contrôler ActiveX est utilisé pour afficher ce contrôle, cette solution ne fonctionnera pas.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Utilisation de l’étiquette CODEBASE avec un fichier INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Un fichier .inf contrôlera l’installation d’un .ocx et de ses fichiers supportifs. Cette méthode n’est pas recommandée car il n’est pas possible de signer un fichier .inf (voir [Code de signature](#_core_signing_code) pour les pointeurs sur la signature du code).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Utilisation de l’étiquette CODEBASE avec un fichier CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Les fichiers ministériels sont le moyen recommandé d’emballer les contrôles ActiveX qui utilisent MFC. L’emballage d’un contrôle MFC ActiveX dans un fichier d’armoire permet d’inclure un fichier .inf pour contrôler l’installation du contrôle ActiveX et de tout DLLs dépendant (comme les DLL MFC). L’utilisation d’un fichier CAB comprime automatiquement le code pour un téléchargement plus rapide. Si vous utilisez un fichier .cab pour le téléchargement de composants, il est plus rapide de signer l’ensemble du fichier .cab que chaque composant individuel.

### <a name="creating-cab-files"></a>Création de fichiers CAB

Les outils pour créer des fichiers coffret font maintenant partie de [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk).

Le fichier de `CODEBASE` cabinet indiqué par devrait contenir le fichier .ocx pour votre contrôle ActiveX et un fichier .inf pour contrôler son installation. Vous créez le fichier du coffre en spécifiant le nom de votre fichier de contrôle et un fichier .inf. N’incluez pas les DLL à charge qui peuvent déjà exister sur le système dans ce fichier du Cabinet. Par exemple, les DLL MFC sont emballés dans un fichier ministériel distinct et mentionnés par le fichier de contrôle .inf.

Pour plus de détails sur la façon de créer un fichier CAB, voir [Créer un fichier CAB](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Le fichier INF

L’exemple suivant, spindial.inf, répertorie les fichiers à l’appui et les informations de version nécessaires pour le contrôle spindial MFC. Notez l’emplacement des LPL MFC est un site Web Microsoft. Le mfc42.cab est fourni et signé par Microsoft.

```
Contents of spindial.inf:
[mfc42installer]
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0
```

### <a name="the-object-tag"></a>L’OBJECTIF \<> Tag

L’exemple suivant illustre `<OBJECT>` l’utilisation de l’étiquette pour emballer le contrôle de l’échantillon spindial MFC.

```
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51
    CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3"
    CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001">
<PARAM NAME="_Version" VALUE="65536">
<PARAM NAME="_ExtentX" VALUE="2646">
<PARAM NAME="_ExtentY" VALUE="1323">
<PARAM NAME="_StockProps" VALUE="0">
<PARAM NAME="NeedlePosition" VALUE="2">
</OBJECT>
```

Dans ce cas, spindial.cab contiendra deux fichiers, spindial.ocx et spindial.inf. La commande suivante établira le dossier du Cabinet :

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

Le `-s 6144` paramètre réserve de l’espace dans le cabinet pour la signature du code.

### <a name="the-version-tag"></a>L’étiquette de version

Notez ici `#Version` que les informations spécifiées avec un fichier CAB `<OBJECT>` s’appliquent au contrôle spécifié par le paramètre *CLASSID* de l’étiquette.

Selon la version spécifiée, vous pouvez forcer le téléchargement de votre contrôle. Pour les spécifications complètes de l’étiquette, `OBJECT` y compris le paramètre *CODEBASE,* voir la référence W3C.

## <a name="marking-a-control-safe-for-scripting-and-initializing"></a><a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Marquage d’un contrôle sûr pour le script et l’initialisation

Les contrôles ActiveX utilisés dans les pages Web doivent être marqués comme sûrs pour le script et sans danger pour l’initialisation si elles sont en fait sûres. Un contrôle sécuritaire n’effectuera pas d’IO de disque ou n’accédera pas directement à la mémoire ou aux registres d’une machine.

Les contrôles peuvent être marqués comme sûrs pour le script et sans danger pour l’initialisation via le registre. Modifier `DllRegisterServer` pour ajouter des entrées similaires à ce qui suit pour marquer le contrôle comme sûr pour le script et la persistance dans le registre. Une autre méthode `IObjectSafety`est de mettre en œuvre .

Vous définirez des GUIDs (Identificateurs uniques mondiaux) pour que votre contrôle le marque sans danger pour le script et la persistance. Les contrôles qui peuvent être scénarisés en toute sécurité contiendront une inscription de registre semblable à ce qui suit :

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Les contrôles qui peuvent être paralysés en toute sécurité à partir de données persistantes sont marqués sans danger pour la persistance avec une entrée de registre similaire à:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Ajoutez des entrées similaires à ce qui suit (en `{06889605-B8D0-101A-91F1-00608CEAD5B3}`remplaçant l’ID de classe de votre contrôle à la place de) pour associer vos clés à l’ID de classe suivant :

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

## <a name="licensing-issues"></a><a name="_core_licensing_issues"></a>Questions de licence

Si vous souhaitez utiliser un contrôle sous licence sur une page Web, vous devez vérifier que l’accord de licence permet son utilisation sur Internet et créer un fichier de paquet de licence (LPK) pour elle.

Un contrôle ActiveX sous licence ne se chargera pas correctement dans une page HTML si l’ordinateur exécutant Internet Explorer n’est pas autorisé à utiliser le contrôle. Par exemple, si un contrôle autorisé a été construit à l’aide de Visual C, la page HTML utilisant le contrôle se chargera correctement sur l’ordinateur où le contrôle a été construit, mais elle ne se chargera pas sur un autre ordinateur à moins que les informations de licence ne soient incluses.

Pour utiliser un contrôle ActiveX sous licence dans Internet Explorer, vous devez vérifier l’accord de licence du fournisseur pour vérifier que la licence pour le contrôle permet :

- Redistribution

- Utilisation du contrôle sur Internet

- Utilisation du paramètre Codebase

Pour utiliser un contrôle sous licence dans une page HTML sur une machine non autorisée, vous devez générer un fichier de paquet de licence (LPK). Le fichier LPK contient des licences de temps d’exécution pour les contrôles sous licence dans la page HTML. Ce fichier est généré via LPK_TOOL. EXE qui est livré avec l’ActiveX SDK.

#### <a name="to-create-an-lpk-file"></a>Pour créer un fichier LPK

1. Exécutez LPK_TOOL. EXE sur un ordinateur qui est autorisé à utiliser le contrôle.

1. Dans la boîte de dialogue de **l’outil d’auteur de paquet de licence,** dans la boîte de liste **de contrôles disponibles,** sélectionnez chaque contrôle ActiveX sous licence qui sera utilisé sur la page HTML et cliquez sur **Ajouter**.

1. Cliquez **sur Enregistrer & Sortie** et tapez un nom pour le fichier LPK. Cela créera le fichier LPK et fermera l’application.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Pour intégrer un contrôle sous licence sur une page HTML

1. Modifiez votre page HTML. Dans la page HTML, insérez une \<étiquette DE> \<OBJECT pour l’objet De gestionnaire de licence avant toute autre> balises OBJECT. Le gestionnaire de licence est un contrôle ActiveX qui est installé avec Internet Explorer. Son ID de classe est indiqué ci-dessous. Définissez la propriété LPKPath de l’objet de gestionnaire de licence sur le chemin et le nom du fichier LPK. Vous ne pouvez avoir qu’un seul fichier LPK par page HTML.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Insérez l’étiquette \<OBJECT> pour votre contrôle sous licence après l’étiquette De gestionnaire de licence.

   Par exemple, une page HTML qui affiche le contrôle Microsoft Masked Edit est affichée ci-dessous. L’ID de première classe est pour le contrôle de gestionnaire de licence, l’ID de deuxième classe est pour le contrôle Masked Edit. Modifiez les balises pour indiquer le chemin relatif du fichier .lpk que vous avez créé plus tôt, et ajoutez une étiquette d’objet comprenant l’ID de classe pour votre contrôle.

1. Insérez l’attribut \<EMBED> pour votre fichier LPK, si vous utilisez le plug-in NCompass ActiveX.

   Si votre contrôle peut être visualisé sur d’autres navigateurs activés Active — par exemple, \<Netscape à l’aide du plug-in NCompass ActiveX — vous devez ajouter la syntaxe EMBED> comme indiqué ci-dessous.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Pour plus d’informations sur les licences de contrôle, voir [ActiveX Controls: Licensing an ActiveX Control](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

## <a name="signing-code"></a><a name="_core_signing_code"></a>Code de signature

La signature du code est conçue pour identifier la source du code et garantir que le code n’a pas changé depuis sa signature. Selon les paramètres de sécurité du navigateur, les utilisateurs peuvent être avertis avant que le code ne soit téléchargé. Les utilisateurs peuvent choisir de faire confiance à certains propriétaires de certificats ou entreprises, auquel cas le code signé par ceux qui ont confiance sera téléchargé sans avertissement. Le code est signé numériquement pour éviter la falsification.

Assurez-vous que votre code final est signé afin que votre contrôle puisse être téléchargé automatiquement sans afficher de messages d’avertissement de confiance. Pour plus de détails sur la façon de signer du code, consultez la documentation sur Authenticode dans l’ActiveX SDK et voir [Signing a CAB File](/windows/win32/devnotes/cabinet-api-functions).

Selon les paramètres de la confiance et du niveau de sécurité du navigateur, un certificat peut être affiché pour identifier la personne ou l’entreprise signataire. Si le niveau de sécurité n’est pas, ou si le titulaire du certificat de contrôle signé est approuvé, un certificat ne sera pas affiché. Consultez [les niveaux de sécurité et le comportement de contrôle des navigateurs Internet Explorer](#_core_internet_explorer_browser_safety_levels_and_control_behavior) pour plus de détails sur la façon dont le paramètre de sécurité du navigateur déterminera si votre contrôle est téléchargé et un certificat affiché.

Le code de garantie numérique n’a pas changé depuis sa signature. Un hachage du code est pris et intégré dans le certificat. Ce hachage est plus tard comparé à un hachage du code pris après le téléchargement du code, mais avant qu’il ne s’exécute. Des entreprises telles que Verisign peuvent fournir des clés privées et publiques nécessaires pour signer du code. L’ActiveX SDK s’expédie avec MakeCert, un utilitaire pour la création de certificats d’essai.

## <a name="managing-the-palette"></a><a name="_core_managing_the_palette"></a>Gestion de la palette

Les conteneurs déterminent la palette et la rendent disponible comme une propriété ambiante, **DISPID_AMBIENT_PALETTE**. Un conteneur (par exemple, Internet Explorer) choisit une palette qui est utilisée par tous les contrôles ActiveX sur une page pour déterminer leur propre palette. Cela empêche le scintillement de l’affichage et présente une apparence cohérente.

Un contrôle peut `OnAmbientPropertyChange` remplacer pour gérer la notification des modifications apportées à la palette.

Un contrôle peut `OnGetColorSet` remplacer pour retourner un ensemble de couleurs pour dessiner la palette. Les conteneurs utilisent la valeur de retour pour déterminer si un contrôle est conscient de la palette.

En vertu des lignes directrices d’OCX 96, un contrôle doit toujours se rendre compte de sa palette en arrière-plan.

Les contenants plus anciens qui n’utilisent pas la propriété de palette ambiante envoient des messages WM_QUERYNEWPALETTE et WM_PALETTECHANGED. Un contrôle peut `OnQueryNewPalette` `OnPaletteChanged` remplacer et gérer ces messages.

## <a name="internet-explorer-browser-safety-levels-and-control-behavior"></a><a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Niveaux de sécurité et contrôle du navigateur Internet Explorer

Un navigateur a des options pour le niveau de sécurité, configurable par l’utilisateur. Étant donné que les pages Web peuvent contenir du contenu actif qui pourrait nuire à l’ordinateur d’un utilisateur, les navigateurs permettent à l’utilisateur de sélectionner des options pour le niveau de sécurité. Selon la façon dont un navigateur implémente les niveaux de sécurité, un contrôle ne peut pas être téléchargé du tout, ou affichera un certificat ou un message d’avertissement pour permettre à l’utilisateur de choisir au moment de l’exécution si oui ou non de télécharger le contrôle. Le comportement des contrôles ActiveX sous des niveaux de sécurité élevés, moyens et faibles sur Internet Explorer est énuméré ci-dessous.

### <a name="high-safety-mode"></a>Mode de sécurité élevé

- Les contrôles non signés ne seront pas téléchargés.

- Les contrôles signés afficheront un certificat s’ils ne font pas confiance (un utilisateur peut choisir une option pour toujours faire confiance au code de ce propriétaire de certificat à partir de maintenant).

- Seuls les contrôles marqués comme sûrs auront des données persistantes et/ou seront scriptables.

### <a name="medium-safety-mode"></a>Mode de sécurité moyen

- Les contrôles non signés afficheront un avertissement avant le téléchargement.

- Les contrôles signés afficheront un certificat s’ils ne sont pas fiables.

- Les contrôles non indiqués comme sûrs afficheront un avertissement.

### <a name="low-safety-mode"></a>Mode de sécurité faible

- Les contrôles sont téléchargés sans avertissement.

- Le script et la persistance se produisent sans avertissement.

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC Internet Programming Basics](../mfc/mfc-internet-programming-basics.md)<br/>
[Contrôles ActiveX MFC : gestion des licences d'un contrôle ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
