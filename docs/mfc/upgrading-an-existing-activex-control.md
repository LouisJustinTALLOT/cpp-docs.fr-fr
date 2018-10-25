---
title: La mise à niveau d’un contrôle ActiveX | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0567913eac57c4150f9fe6d051d2fc8e0e31860b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082925"
---
# <a name="upgrading-an-existing-activex-control"></a>Mise à niveau d'un contrôle ActiveX

Contrôles ActiveX existant (anciennement contrôles OLE) peut être utilisé sur Internet sans modification. Toutefois, vous souhaiterez modifier des contrôles afin d’améliorer leurs performances.

> [!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent les ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Lorsque vous utilisez votre contrôle sur une page Web, il existe des considérations supplémentaires. Le fichier .ocx et tous les fichiers de prise en charge doivent se trouver sur l’ordinateur cible ou être téléchargés sur Internet. Cela rend la taille du code et un aspect important de temps de téléchargement. Téléchargements peuvent être empaquetés dans un fichier .cab signé. Vous pouvez marquer votre contrôle comme sûrs pour l’écriture de scripts et l’initialisation.

Cet article aborde les rubriques suivantes :

- [Empaqueter le Code pour le téléchargement](#_core_packaging_code_for_downloading)

- [Marquage de contrôle sécurisé pour les scripts et l’initialisation](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problèmes de licence](#_core_licensing_issues)

- [Signature du Code](#_core_signing_code)

- [Gestion de la Palette](#_core_managing_the_palette)

- [Niveaux de sécurité du navigateur Internet Explorer et de contrôler le comportement](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Vous pouvez également ajouter des optimisations, comme décrit dans [contrôles ActiveX : optimisation](../mfc/mfc-activex-controls-optimization.md). Monikers peuvent être utilisées pour télécharger des propriétés et des objets BLOB volumineux en mode asynchrone, comme décrit dans [contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md).

##  <a name="_core_packaging_code_for_downloading"></a> Empaqueter le Code pour le téléchargement

Pour plus d’informations sur ce sujet, consultez [empaquetage des contrôles ActiveX](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>La balise CODEBASE

Contrôles ActiveX sont incorporés dans les pages Web à l’aide de la `<OBJECT>` balise. Le `CODEBASE` paramètre de la `<OBJECT>` balise spécifie l’emplacement à partir duquel télécharger le contrôle. `CODEBASE` peut pointer vers un nombre de différents types de fichiers avec succès.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>À l’aide de la balise CODEBASE avec un fichier OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Cette solution télécharge uniquement les fichiers .ocx du contrôle et nécessite toutes les DLL prise en charge déjà être installé sur l’ordinateur client. Cela fonctionne pour Internet Explorer et MFC les contrôles ActiveX générées avec Visual C++, car Internet Explorer est fourni avec les DLL de prise en charge pour les contrôles de Visual C++. Si un autre navigateur Internet qui est compatible avec les contrôles d’ActiveX est utilisé pour afficher ce contrôle, cette solution ne fonctionnera pas.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>À l’aide de la balise CODEBASE avec un fichier INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Un fichier .inf contrôle l’installation d’un .ocx et ses fichiers de prise en charge. Cette méthode n’est pas recommandée, car il n’est pas possible de signer un fichier .inf (consultez [de signature de Code](#_core_signing_code) pour les pointeurs sur la signature de code).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>À l’aide de la balise CODEBASE avec un fichier CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Fichiers CAB sont la méthode recommandée pour les contrôles ActiveX de package qui utilisent MFC. Empaquetage d’un contrôle ActiveX MFC dans un fichier CAB permet à un fichier .inf être inclus pour contrôler l’installation du contrôle ActiveX et toutes les DLL dépendantes (telles que les DLL MFC). À l’aide d’un fichier CAB automatiquement compresse le code pour accélérer le téléchargement. Si vous utilisez un fichier .cab pour le téléchargement de composants, il est plus rapide pour signer le fichier .cab tout entier plutôt que chaque composant.

### <a name="creating-cab-files"></a>Création de fichiers CAB

Outils pour créer des fichiers CAB sont désormais partie de la [SDK Windows 10](https://dev.windows.com/downloads/windows-10-sdk).

Le fichier cab vers lequel pointe `CODEBASE` doit contenir le fichier .ocx pour votre contrôle ActiveX et un fichier .inf pour contrôler son installation. Vous créez le fichier CAB en spécifiant le nom de votre fichier de contrôle et un fichier .inf. N’incluez pas les DLL dépendantes qui existent déjà sur le système dans le fichier CAB. Par exemple, les DLL MFC sont empaquetées dans un fichier CAB distinct et référencés par le fichier .inf du contrôle.

Pour plus d’informations sur la création d’un fichier CAB, consultez [création d’un fichier CAB](/windows/desktop/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Le fichier INF

L’exemple suivant, spindial.inf, répertorie les fichiers de prise en charge et les informations de version nécessitent pour le Spindial MFC contrôler. Notez que l’emplacement pour les DLL MFC est un site Web de Microsoft. Le fichier mfc42.cab est fourni et signé par Microsoft.

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

### <a name="the-object-tag"></a>Le \<objet > balise

L’exemple suivant illustre l’utilisation de la `<OBJECT>` balise pour empaqueter l’exemple de contrôle Spindial MFC.

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

Dans ce cas, spindial.cab contiendra deux fichiers, spindial.ocx et spindial.inf. La commande suivante génère le fichier CAB :

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

Le `-s 6144` paramètre réserve l’espace dans le fichier CAB pour la signature de code.

### <a name="the-version-tag"></a>La balise de Version

Notez ici que la `#Version` informations spécifiées avec un fichier CAB s’applique au contrôle spécifié par le *CLASSID* paramètre de la `<OBJECT>` balise.

Selon la version spécifiée, vous pouvez forcer le téléchargement de votre contrôle. Pour des spécifications complètes de la `OBJECT` balise, y compris le *CODEBASE* paramètre, consultez le W3C référence.

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> Marquage de contrôle sécurisé pour les scripts et l’initialisation

Contrôles ActiveX utilisés dans les pages Web doivent être marqués comme sécurisé pour le script et l’initialisation s’ils sont en fait sans échec. Un contrôle sécurisé ne sera pas effectuer d’e/s de disque ou accéder directement à la mémoire ou les registres d’une machine.

Contrôles peuvent être marqués comme sécurisés pour les scripts et l’initialisation via le Registre. Modifier `DllRegisterServer` pour ajouter des entrées similaires à ce qui suit pour marquer le contrôle comme sûrs pour l’écriture de scripts et la persistance dans le Registre. Une autre méthode consiste à implémenter `IObjectSafety`.

Vous allez définir le GUID (Globally Unique Identifiers) pour votre contrôle marquer sécurisé pour les scripts et la persistance. Les contrôles qui peuvent être scriptés en toute sécurité contient une entrée de Registre similaire à ce qui suit :

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Les contrôles qui peuvent être initialisés en toute sécurité à partir de données persistantes sont reconnus sûrs pour la persistance avec une entrée de Registre similaire à :

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Ajouter des entrées similaires à ce qui suit (ID à la place de la classe de substitution de votre contrôle `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) pour associer vos clés avec l’ID de classe suivant :

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a> Problèmes de licence

Si vous souhaitez utiliser un contrôle sous licence sur une page Web, vous devez vérifier que le contrat de licence permet son utilisation sur Internet et de créer un fichier de package de licence (LPK) pour celle-ci.

Un contrôle ActiveX sous licence ne chargera pas correctement dans une page HTML si l’ordinateur qui exécute Internet Explorer n’est pas sous licence pour utiliser le contrôle. Par exemple, si un contrôle sous licence a été créé à l’aide de Visual C++, la page HTML à l’aide du contrôle chargera correctement sur l’ordinateur où le contrôle a été créé, mais il ne chargera pas sur un autre ordinateur, sauf si les informations de licence sont incluses.

Pour utiliser un contrôle ActiveX sous licence dans Internet Explorer, vous devez vérifier le contrat de licence du fournisseur pour vérifier que la licence pour le contrôle autorise :

- Redistribution

- Utilisation du contrôle sur Internet

- Utilisation du paramètre de base de code

Pour utiliser un contrôle sous licence dans une page HTML sur un ordinateur sans licence, vous devez générer un fichier de package de licence (LPK). Ce fichier contient les licences d’exécution pour les contrôles sous licence dans la page HTML. Ce fichier est généré Lpk_tool. EXE qui est fourni avec le SDK ActiveX. Pour plus d’informations, consultez le site Web MSDN à l’adresse [ http://msdn.microsoft.com ](http://msdn.microsoft.com).

#### <a name="to-create-an-lpk-file"></a>Pour créer un fichier LPK

1. Exécutez LPK_TOOL. EXE sur un ordinateur qui est concédé sous licence pour utiliser le contrôle.

1. Dans le **outil de création de Package de licence** boîte de dialogue le **contrôles disponibles** zone de liste, sélectionnez chaque licence contrôle ActiveX qui sera utilisé dans la page HTML et cliquez sur **ajouter**.

1. Cliquez sur **enregistrer et quitter** et tapez un nom pour le fichier LPK. Cela crée le fichier LPK et fermez l’application.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Pour incorporer un contrôle sous licence sur une page HTML

1. Modifier votre page HTML. Dans la page HTML, insérez un \<objet > balise pour l’objet de gestionnaire de licences avant toute autre \<objet > balises. Le Gestionnaire de licences est un contrôle ActiveX qui est installé avec Internet Explorer. Son ID de classe est indiqué ci-dessous. Définissez la propriété LPKPath de l’objet de gestionnaire de licences pour le chemin d’accès et le nom du fichier LPK. Vous pouvez avoir qu’un seul fichier LPK par page HTML.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Insérer le \<objet > balise pour votre contrôle sous licence après la balise de gestionnaire de licences.

   Par exemple, une page HTML qui affiche le contrôle Microsoft Masked Edit est indiquée ci-dessous. Le premier identificateur de classe qu'est pour le contrôle de gestionnaire de licences, le deuxième identificateur de classe qu'est pour le contrôle Masked Edit. Modifier les balises pour pointer vers le chemin d’accès relatif du fichier d’interactivité que vous avez créé précédemment et ajoutez une balise d’objet, y compris l’ID de classe de votre contrôle.

1. Insérer le \<EMBED > attribut pour le fichier LPK, si vous utilisez le module complémentaire NCompass ActiveX.

   Si votre contrôle peut être affiché sur les autres actif activé navigateurs — par exemple, Netscape utilisant le module complémentaire NCompass ActiveX — vous devez ajouter le \<EMBED > syntaxe comme illustré ci-dessous.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Pour plus d’informations sur les licences de contrôle, consultez [contrôles ActiveX : gestion des licences un contrôle ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

##  <a name="_core_signing_code"></a> Signature du Code

Signature de code est conçue pour identifier la source de code, et pour garantir que le code n’a pas changé depuis qu’il a été signé. En fonction des paramètres de sécurité du navigateur, les utilisateurs peuvent être avertis avant le téléchargement du code. Les utilisateurs peuvent choisir d’approuver certains propriétaires de certificat ou les entreprises, dans lequel cas le code signé par ceux approuvé seront téléchargés sans avertissement. Code est signé numériquement pour éviter toute falsification.

Assurez-vous que votre code final est signé afin que votre contrôle peut être téléchargé automatiquement sans afficher les messages d’avertissement de niveau de confiance. Pour plus d’informations sur la façon de signer le code, consultez la documentation sur Authenticode dans le SDK ActiveX et consultez [signature d’un fichier CAB](/windows/desktop/devnotes/cabinet-api-functions).

En fonction de l’approbation et navigateur au niveau paramètres de sécurité, un certificat peut être affiché pour identifier la personne ou société signataire. Si le niveau de sécurité est none, ou si le propriétaire du certificat du contrôle signé est approuvé, un certificat ne sera pas affiché. Consultez [niveaux de sécurité du navigateur Internet Explorer et de contrôler le comportement](#_core_internet_explorer_browser_safety_levels_and_control_behavior) pour plus d’informations sur la façon dont le paramètre de sécurité du navigateur déterminera si votre contrôle est téléchargé et un certificat est affiché.

Digital Signature garantit que le code n’a pas changé dans la mesure où il a été signé. Un hachage du code est effectué et incorporé dans le certificat. Ce hachage est comparé ultérieurement avec un hachage du code pris après le téléchargement du code, mais avant son exécution. Sociétés telles que Verisign peuvent fournir des clés publiques et privées nécessaires pour signer le code. Le SDK ActiveX est livré avec MakeCert, un utilitaire de création de certificats de test.

##  <a name="_core_managing_the_palette"></a> Gestion de la Palette

Conteneurs déterminent la palette et le rendre disponible comme une propriété ambiante, **DISPID_AMBIENT_PALETTE**. Un conteneur (par exemple, Internet Explorer) choisit une palette est utilisée par tous les contrôles ActiveX sur une page pour déterminer leur propre palette. Cela empêche le scintillement de l’affichage et présente une apparence cohérente.

Un contrôle peut substituer `OnAmbientPropertyChange` pour gérer la notification des modifications apportées à la palette.

Un contrôle peut substituer `OnGetColorSet` pour retourner un jeu pour dessiner la palette de couleurs. Conteneurs utilisent la valeur de retour pour déterminer si un contrôle est compatible avec la palette.

Sous les directives OCX 96, un contrôle doit toujours réaliser sa palette en arrière-plan.

Les conteneurs plus anciens qui n’utilisent pas la propriété ambiante palette envoient les messages WM_QUERYNEWPALETTE et WM_PALETTECHANGED. Un contrôle peut substituer `OnQueryNewPalette` et `OnPaletteChanged` pour gérer ces messages.

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Niveaux de sécurité du navigateur Internet Explorer et de contrôler le comportement

Un navigateur a des options de niveau de sécurité configurable par l’utilisateur. Étant donné que les pages Web peuvent contenir un contenu actif qui peut endommager l’ordinateur d’un utilisateur, navigateurs autorisent l’utilisateur à sélectionner les options de niveau de sécurité. Selon la façon dont un navigateur implémente des niveaux de sécurité, un contrôle ne peut-être pas être téléchargé du tout, ou affiche un certificat ou un message d’avertissement pour autoriser l’utilisateur de choisir au moment de l’exécution, s’il faut télécharger le contrôle. Le comportement des contrôles ActiveX sous des niveaux de sécurité élevé, moyen et faible dans Internet Explorer est indiqué ci-dessous.

### <a name="high-safety-mode"></a>Mode haute sécurité

- Contrôles non signés ne seront pas téléchargés.

- Contrôles signés affichent un certificat si non approuvés (un utilisateur peut choisir une option pour approuver systématiquement le code à partir de ce propriétaire de certificat par la suite).

- Seuls les contrôles marqués comme sécurisés seront contiennent des données persistantes et/ou scriptable.

### <a name="medium-safety-mode"></a>Mode de sécurité moyen

- Contrôles non signés affiche un avertissement avant de télécharger.

- Contrôles signés affichent un certificat si non approuvés.

- Contrôles non marqués comme sécurisés affiche un avertissement.

### <a name="low-safety-mode"></a>Mode de sécurité faible

- Les contrôles sont téléchargés sans avertissement.

- Scripts et la persistance surviennent sans avertissement.

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Contrôles ActiveX MFC : gestion des licences d’un contrôle ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

