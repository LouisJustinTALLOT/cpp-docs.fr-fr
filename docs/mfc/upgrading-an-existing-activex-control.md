---
description: 'En savoir plus sur : mise à niveau d’un contrôle ActiveX existant'
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
ms.openlocfilehash: aeff78eca2c88bea9bcceb7ac6f79e907c141350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263684"
---
# <a name="upgrading-an-existing-activex-control"></a>Mise à niveau d'un contrôle ActiveX

Les contrôles ActiveX existants (anciennement contrôles OLE) peuvent être utilisés sur Internet sans modification. Toutefois, vous souhaiterez peut-être modifier les contrôles pour améliorer leurs performances.

> [!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Lorsque vous utilisez votre contrôle sur une page Web, des considérations supplémentaires sont à prendre en compte. Le fichier. ocx et tous les fichiers de prise en charge doivent se trouver sur l’ordinateur cible ou être téléchargés sur Internet. La taille du code et le temps de téléchargement sont donc importants. Les téléchargements peuvent être empaquetés dans un fichier. cab signé. Vous pouvez marquer votre contrôle comme étant sécurisé pour l’écriture de scripts et en toute sécurité pour l’initialisation.

Cet article aborde les thèmes suivants :

- [Empaquetage du code pour le téléchargement](#_core_packaging_code_for_downloading)

- [Marquage d’un contrôle comme sécurisé pour l’écriture de scripts et l’initialisation](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problèmes liés aux licences](#_core_licensing_issues)

- [Code de signature](#_core_signing_code)

- [Gestion de la palette](#_core_managing_the_palette)

- [Niveau de sécurité du navigateur Internet Explorer et comportement de contrôle](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Vous pouvez également ajouter des optimisations, comme décrit dans [contrôles ActiveX : optimisation](../mfc/mfc-activex-controls-optimization.md). Les monikers peuvent être utilisés pour télécharger des propriétés et des objets BLOB volumineux de manière asynchrone, comme décrit dans [contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md).

## <a name="packaging-code-for-downloading"></a><a name="_core_packaging_code_for_downloading"></a> Empaquetage du code pour le téléchargement

Pour plus d’informations sur ce sujet, consultez [empaquetage de contrôles ActiveX](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>La balise de code base

Les contrôles ActiveX sont incorporés dans des pages Web à l’aide de la `<OBJECT>` balise. Le `CODEBASE` paramètre de la `<OBJECT>` balise spécifie l’emplacement à partir duquel le contrôle doit être téléchargé. `CODEBASE` peut pointer vers un certain nombre de types de fichiers différents.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Utilisation de la balise code base avec un fichier OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Cette solution ne télécharge que le fichier. ocx du contrôle et nécessite que toutes les dll de prise en charge soient déjà installées sur l’ordinateur client. Cela fonctionne pour Internet Explorer et les contrôles ActiveX MFC générés avec Visual C++, car Internet Explorer est fourni avec les dll de prise en charge pour les contrôles Visual C++. Si un autre navigateur Internet prenant en charge les contrôles ActiveX est utilisé pour afficher ce contrôle, cette solution ne fonctionnera pas.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Utilisation de la balise code base avec un fichier INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Un fichier. inf contrôlera l’installation d’un fichier. ocx et de ses fichiers de prise en charge. Cette méthode n’est pas recommandée, car il n’est pas possible de signer un fichier. inf (consultez [signature du code](#_core_signing_code) pour les pointeurs sur la signature du code).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Utilisation de la balise code base avec un fichier CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Les fichiers CAB sont la méthode recommandée pour empaqueter des contrôles ActiveX qui utilisent MFC. L’empaquetage d’un contrôle ActiveX MFC dans un fichier CAB permet à un fichier. inf d’être inclus pour contrôler l’installation du contrôle ActiveX et des dll dépendantes (telles que les DLL MFC). L’utilisation d’un fichier CAB compresse automatiquement le code pour accélérer le téléchargement. Si vous utilisez un fichier. cab pour le téléchargement de composants, il est plus rapide de signer le fichier. cab entier que chaque composant individuel.

### <a name="creating-cab-files"></a>Création de fichiers CAB

Les outils permettant de créer des fichiers CAB font désormais partie du [Kit de développement logiciel (SDK) Windows 10](https://dev.windows.com/downloads/windows-10-sdk).

Le fichier CAB vers lequel pointe `CODEBASE` doit contenir le fichier. ocx pour votre contrôle ActiveX et un fichier. inf pour contrôler son installation. Vous créez le fichier CAB en spécifiant le nom de votre fichier de contrôle et un fichier. inf. N’incluez pas les dll dépendantes qui peuvent déjà exister sur le système dans ce fichier CAB. Par exemple, les DLL MFC sont empaquetées dans un fichier cab distinct et référencées par le fichier Control. inf.

Pour plus d’informations sur la création d’un fichier CAB, consultez [création d’un fichier CAB](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Fichier INF

L’exemple suivant, spindial. inf, répertorie les fichiers de prise en charge et les informations de version nécessaires pour le contrôle MFC spindial. Notez que l’emplacement des DLL MFC est un site Web Microsoft. Le mfc42.cab est fourni et signé par Microsoft.

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

### <a name="the-object-tag"></a>La \<OBJECT> balise

L’exemple suivant illustre l’utilisation de la `<OBJECT>` balise pour empaqueter l’exemple de contrôle MFC spindial.

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

Dans ce cas, spindial.cab contiendra deux fichiers, spindial. ocx et spindial. inf. La commande suivante génère le fichier CAB :

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

Le `-s 6144` paramètre réserve de l’espace dans le fichier CAB pour la signature de code.

### <a name="the-version-tag"></a>La balise de version

Notez ici que les `#Version` informations spécifiées avec un fichier CAB s’appliquent au contrôle spécifié par le paramètre *ClassID* de la `<OBJECT>` balise.

Selon la version spécifiée, vous pouvez forcer le téléchargement de votre contrôle. Pour obtenir les spécifications complètes de la `OBJECT` balise, y compris le paramètre *code base* , consultez la référence du W3C.

## <a name="marking-a-control-safe-for-scripting-and-initializing"></a><a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> Marquage d’un contrôle comme sécurisé pour l’écriture de scripts et l’initialisation

Les contrôles ActiveX utilisés dans les pages Web doivent être marqués comme sécurisés pour l’écriture de scripts et sûrs pour l’initialisation s’ils sont en fait sécurisés. Un contrôle sécurisé n’effectue pas d’e/s disque ou n’accède pas directement à la mémoire ou aux registres d’un ordinateur.

Les contrôles peuvent être marqués comme sécurisés pour l’écriture de scripts et sûrs pour l’initialisation via le registre. Modifiez `DllRegisterServer` pour ajouter des entrées similaires à ce qui suit afin de marquer le contrôle comme étant sûr pour l’écriture de scripts et la persistance dans le registre. Une autre méthode consiste à implémenter `IObjectSafety` .

Vous allez définir des GUID (identificateurs globaux uniques) pour votre contrôle afin de le marquer comme sécurisé pour l’écriture de scripts et la persistance. Les contrôles qui peuvent être scriptés en toute sécurité contiendront une entrée de registre semblable à la suivante :

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Les contrôles qui peuvent être initialisés en toute sécurité à partir de données persistantes sont marqués comme sécurisés pour la persistance avec une entrée de Registre similaire à celle-ci :

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Ajoutez des entrées similaires à ce qui suit (en remplaçant l’ID de classe de votre contrôle à la place de `{06889605-B8D0-101A-91F1-00608CEAD5B3}` ) pour associer vos clés à l’ID de classe suivant :

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

## <a name="licensing-issues"></a><a name="_core_licensing_issues"></a> Problèmes liés aux licences

Si vous souhaitez utiliser un contrôle sous licence sur une page Web, vous devez vérifier que le contrat de licence autorise son utilisation sur Internet et créer un fichier de package de licence (LPK) pour celui-ci.

Un contrôle ActiveX sous licence ne se chargera pas correctement dans une page HTML si l’ordinateur exécutant Internet Explorer n’a pas de licence d’utilisation du contrôle. Par exemple, si un contrôle sous licence a été créé à l’aide de Visual C++, la page HTML qui utilise le contrôle se chargera correctement sur l’ordinateur sur lequel le contrôle a été créé, mais elle ne sera pas chargée sur un autre ordinateur, sauf si les informations de licence sont incluses.

Pour utiliser un contrôle ActiveX sous licence dans Internet Explorer, vous devez vérifier le contrat de licence du fournisseur pour vérifier que la licence du contrôle le permet :

- Redistribution

- Utilisation du contrôle sur Internet

- Utilisation du paramètre CODEBASE

Pour utiliser un contrôle sous licence dans une page HTML sur un ordinateur sans licence, vous devez générer un fichier de package de licences (LPK). Le fichier LPK contient des licences d’exécution pour les contrôles sous licence dans la page HTML. Ce fichier est généré via LPK_TOOL.EXE qui est fourni avec le kit de développement logiciel (SDK) ActiveX.

#### <a name="to-create-an-lpk-file"></a>Pour créer un fichier LPK

1. Exécutez LPK_TOOL.EXE sur un ordinateur qui dispose d’une licence pour utiliser le contrôle.

1. Dans la boîte de dialogue **outil de création de package de licences** , dans la zone de liste **contrôles disponibles** , sélectionnez chaque contrôle ActiveX sous licence qui sera utilisé dans la page HTML, puis cliquez sur **Ajouter**.

1. Cliquez sur **enregistrer & quitter** et tapez un nom pour le fichier LPK. Cette opération crée le fichier LPK et ferme l’application.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Pour incorporer un contrôle sous licence sur une page HTML

1. Modifiez votre page HTML. Dans la page HTML, insérez une \<OBJECT> balise pour l’objet gestionnaire de licences avant toute autre balise \<OBJECT> . Le gestionnaire de licences est un contrôle ActiveX qui est installé avec Internet Explorer. Son ID de classe est indiqué ci-dessous. Définissez la propriété LPKPath de l’objet gestionnaire de licences sur le chemin d’accès et le nom du fichier LPK. Vous ne pouvez avoir qu’un seul fichier LPK par page HTML.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Insérez la \<OBJECT> balise pour votre contrôle sous licence après la balise du gestionnaire de licences.

   Par exemple, une page HTML qui affiche le contrôle d’édition masqué de Microsoft est illustrée ci-dessous. Le premier ID de classe est pour le contrôle du gestionnaire de licences, le deuxième ID de classe est pour le contrôle d’édition masqué. Modifiez les balises pour qu’elles pointent vers le chemin d’accès relatif du fichier. lpk que vous avez créé précédemment, puis ajoutez une balise d’objet incluant l’ID de classe de votre contrôle.

1. Insérez l' \<EMBED> attribut de votre fichier LPK, si vous utilisez le plug-in ActiveX NCompass.

   Si votre contrôle peut être affiché sur d’autres navigateurs activés, par exemple Netscape à l’aide du plug-in ActiveX NCompass, vous devez ajouter la \<EMBED> syntaxe comme indiqué ci-dessous.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Pour plus d’informations sur le contrôle des licences, consultez [contrôles ActiveX : gestion des licences d’un contrôle ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

## <a name="signing-code"></a><a name="_core_signing_code"></a> Code de signature

La signature de code est conçue pour identifier la source de code et garantir que le code n’a pas changé depuis sa signature. Selon les paramètres de sécurité du navigateur, les utilisateurs peuvent être avertis avant le téléchargement du code. Les utilisateurs peuvent choisir d’approuver certains propriétaires ou sociétés de certificats, auquel cas le code signé par ces certificats de confiance est téléchargé sans avertissement. Le code est signé numériquement pour éviter toute falsification.

Assurez-vous que votre code final est signé afin que votre contrôle puisse être automatiquement téléchargé sans afficher de messages d’avertissement de confiance. Pour plus d’informations sur la façon de signer le code, consultez la documentation sur Authenticode dans le kit de développement logiciel (SDK) ActiveX et consultez [signature d’un fichier CAB](/windows/win32/devnotes/cabinet-api-functions).

En fonction des paramètres de niveau de sécurité de l’approbation et du navigateur, un certificat peut être affiché pour identifier la personne ou la société signataire. Si le niveau de sécurité est aucun, ou si le propriétaire du certificat du contrôle signé est approuvé, aucun certificat n’est affiché. Pour plus d’informations sur la façon dont le paramètre de sécurité du navigateur détermine si votre contrôle est téléchargé et si un certificat s’affiche, consultez [niveaux de sécurité et contrôle du navigateur Internet Explorer](#_core_internet_explorer_browser_safety_levels_and_control_behavior) .

La signature numérique garantit que le code n’a pas été modifié depuis sa signature. Un hachage du code est pris et incorporé dans le certificat. Ce hachage est par la suite comparé à un hachage du code pris après le téléchargement du code, mais avant son exécution. Des entreprises telles que VeriSign peuvent fournir des clés privées et publiques nécessaires pour signer le code. Le kit de développement logiciel (SDK) ActiveX est fourni avec MakeCert, un utilitaire permettant de créer des certificats de test.

## <a name="managing-the-palette"></a><a name="_core_managing_the_palette"></a> Gestion de la palette

Les conteneurs déterminent la palette et la rendent disponible en tant que propriété ambiante, **DISPID_AMBIENT_PALETTE**. Un conteneur (par exemple, Internet Explorer) choisit une palette qui est utilisée par tous les contrôles ActiveX sur une page pour déterminer leur propre palette. Cela empêche le scintillement de l’affichage et présente une apparence cohérente.

Un contrôle peut être substitué `OnAmbientPropertyChange` pour gérer la notification des modifications apportées à la palette.

Un contrôle peut être substitué `OnGetColorSet` pour retourner un jeu de couleurs pour dessiner la palette. Les conteneurs utilisent la valeur de retour pour déterminer si un contrôle prend en charge la palette.

Sous les instructions OCX 96, un contrôle doit toujours réaliser sa palette en arrière-plan.

Les conteneurs plus anciens qui n’utilisent pas la propriété de palette ambiante envoient des messages WM_QUERYNEWPALETTE et WM_PALETTECHANGED. Un contrôle peut substituer `OnQueryNewPalette` et `OnPaletteChanged` gérer ces messages.

## <a name="internet-explorer-browser-safety-levels-and-control-behavior"></a><a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Niveau de sécurité du navigateur Internet Explorer et comportement de contrôle

Un navigateur possède des options de niveau de sécurité configurables par l’utilisateur. Étant donné que les pages Web peuvent contenir du contenu actif susceptible d’endommager l’ordinateur d’un utilisateur, les navigateurs permettent à l’utilisateur de sélectionner des options pour le niveau de sécurité. Selon la façon dont un navigateur implémente les niveaux de sécurité, un contrôle peut ne pas être téléchargé ou afficher un certificat ou un message d’avertissement pour permettre à l’utilisateur de choisir au moment de l’exécution s’il souhaite ou non Télécharger le contrôle. Le comportement des contrôles ActiveX avec des niveaux de sécurité élevé, moyen et faible sur Internet Explorer est indiqué ci-dessous.

### <a name="high-safety-mode"></a>Mode haute sécurité

- Les contrôles non signés ne seront pas téléchargés.

- Les contrôles signés affichent un certificat s’ils ne sont pas approuvés (un utilisateur peut choisir une option pour toujours faire confiance au code à partir de ce propriétaire de certificat à partir de maintenant).

- Seuls les contrôles marqués comme sécurisés ont des données persistantes et/ou peuvent être scriptables.

### <a name="medium-safety-mode"></a>Mode de sécurité moyen

- Les contrôles non signés affichent un avertissement avant le téléchargement.

- Les contrôles signés affichent un certificat s’ils ne sont pas approuvés.

- Les contrôles qui ne sont pas marqués comme sécurisés affichent un avertissement.

### <a name="low-safety-mode"></a>Mode de sécurité faible

- Les contrôles sont téléchargés sans avertissement.

- L’écriture de scripts et la persistance se produisent sans avertissement.

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Concepts de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Contrôles ActiveX MFC : gestion des licences d’un contrôle ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
