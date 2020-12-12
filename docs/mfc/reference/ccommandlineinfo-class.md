---
description: 'En savoir plus sur : classe CCommandLineInfo'
title: CCommandLineInfo, classe
ms.date: 11/04/2016
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
ms.openlocfilehash: 4c26ae86608725caa61ad4d1077bed01a3f40385
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227921"
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo, classe

Contribue à l'analyse de la ligne de commande au démarrage de l'application.

## <a name="syntax"></a>Syntaxe

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Construit un objet par défaut `CCommandLineInfo` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Remplacez ce rappel pour analyser des paramètres individuels.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCommandLineInfo :: m_bRunAutomated](#m_brunautomated)|Indique que l’option de ligne de commande `/Automation` a été trouvée.|
|[CCommandLineInfo :: m_bRunEmbedded](#m_brunembedded)|Indique que l’option de ligne de commande `/Embedding` a été trouvée.|
|[CCommandLineInfo :: m_bShowSplash](#m_bshowsplash)|Indique si un écran de démarrage doit être affiché.|
|[CCommandLineInfo :: m_nShellCommand](#m_nshellcommand)|Indique la commande d’interpréteur de commandes à traiter.|
|[CCommandLineInfo :: m_strDriverName](#m_strdrivername)|Indique le nom du pilote si la commande d’environnement est imprimer sur ; Sinon, vide.|
|[CCommandLineInfo :: m_strFileName](#m_strfilename)|Indique le nom du fichier à ouvrir ou à imprimer ; vide si la commande d’interpréteur de commandes est nouvelle ou DDE.|
|[CCommandLineInfo :: m_strPortName](#m_strportname)|Indique le nom du port si la commande d’environnement est imprimer vers ; Sinon, vide.|
|[CCommandLineInfo :: m_strPrinterName](#m_strprintername)|Indique le nom de l’imprimante si la commande de l’interpréteur de commandes est imprimer ; Sinon, vide.|
|[CCommandLineInfo :: m_strRestartIdentifier](#m_strrestartidentifier)|Indique l’identificateur de redémarrage unique du gestionnaire de redémarrage si le gestionnaire de redémarrage a redémarré l’application.|

## <a name="remarks"></a>Notes

Une application MFC crée généralement une instance locale de cette classe dans la fonction [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) de son objet application. Cet objet est ensuite passé à [CWinApp ::P arsecommandline](../../mfc/reference/cwinapp-class.md#parsecommandline), qui appelle à plusieurs reprises [ParseParam](#parseparam) pour remplir l' `CCommandLineInfo` objet. L' `CCommandLineInfo` objet est ensuite passé à [CWinApp ::P rocessshellcommand](../../mfc/reference/cwinapp-class.md#processshellcommand) pour gérer les arguments de ligne de commande et les indicateurs.

Vous pouvez utiliser cet objet pour encapsuler les options de ligne de commande et les paramètres suivants :

|Argument de ligne de commande|Commande exécutée|
|----------------------------|----------------------|
|*app*|Nouveau fichier.|
|nom de fichier de l' *application*|Ouvrez le fichier.|
|*application* `/p` extension|Imprimez le fichier sur l’imprimante par défaut.|
|*application* `/pt` nom du port du pilote d’imprimante|Imprimez le fichier sur l’imprimante spécifiée.|
|*application*`/dde`|Commande de démarrage et d’attente DDE.|
|*application*`/Automation`|Démarrez en tant que serveur OLE Automation.|
|*application*`/Embedding`|Démarrez pour modifier un élément OLE incorporé.|
|*application*`/Register`<br /><br /> *application*`/Regserver`|Indique à l’application d’effectuer toutes les tâches d’inscription.|
|*application*`/Unregister`<br /><br /> *application*`/Unregserver`|Indique à l’application d’effectuer toutes les tâches d’annulation de l’inscription.|

Dérivez une nouvelle classe de `CCommandLineInfo` pour gérer d’autres indicateurs et valeurs de paramètre. Remplacez [ParseParam](#parseparam) pour gérer les nouveaux indicateurs.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a> CCommandLineInfo::CCommandLineInfo

Ce constructeur crée un `CCommandLineInfo` objet avec les valeurs par défaut.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Notes

La valeur par défaut consiste à afficher l’écran de démarrage ( `m_bShowSplash=TRUE` ) et à exécuter la commande nouveau dans le menu fichier ( `m_nShellCommand` **= NewFile**).

L’infrastructure d’application appelle [ParseParam](#parseparam) pour remplir les données membres de cet objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a> CCommandLineInfo :: m_bRunAutomated

Indique que l' `/Automation` indicateur a été trouvé sur la ligne de commande.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, cela signifie qu’il démarre en tant que serveur OLE Automation.

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a> CCommandLineInfo :: m_bRunEmbedded

Indique que l' `/Embedding` indicateur a été trouvé sur la ligne de commande.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, cela signifie démarrer pour la modification d’un élément OLE incorporé.

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a> CCommandLineInfo :: m_bShowSplash

Indique que l’écran de démarrage doit être affiché.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, cela signifie que l’écran de démarrage de cette application doit être affiché au démarrage. L’implémentation par défaut de [ParseParam](#parseparam) affecte la valeur true à ce membre de données si [m_nShellCommand](#m_nshellcommand) est égal à `CCommandLineInfo::FileNew` .

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a> CCommandLineInfo :: m_nShellCommand

Indique la commande d’interpréteur de commandes pour cette instance de l’application.

```
m_nShellCommand;
```

### <a name="remarks"></a>Notes

Le type de ce membre de données est le type énuméré suivant, qui est défini dans la `CCommandLineInfo` classe.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

Pour obtenir une brève description de ces valeurs, consultez la liste suivante.

- `CCommandLineInfo::FileNew` Indique qu’aucun nom de fichier n’a été trouvé sur la ligne de commande.

- `CCommandLineInfo::FileOpen` Indique qu’un nom de fichier a été trouvé sur la ligne de commande et qu’aucun des indicateurs suivants n’a été trouvé sur la ligne de commande : `/p` , `/pt` , `/dde` .

- `CCommandLineInfo::FilePrint` Indique que l' `/p` indicateur a été trouvé sur la ligne de commande.

- `CCommandLineInfo::FilePrintTo` Indique que l' `/pt` indicateur a été trouvé sur la ligne de commande.

- `CCommandLineInfo::FileDDE` Indique que l' `/dde` indicateur a été trouvé sur la ligne de commande.

- `CCommandLineInfo::AppRegister` Indique que l' `/Register` `/Regserver` indicateur ou a été trouvé sur la ligne de commande et que l’application a été invitée à s’inscrire.

- `CCommandLineInfo::AppUnregister` Indique que l' `/Unregister` `/Unregserver` application ou a été invité à annuler l’inscription.

- `CCommandLineInfo::RestartByRestartManager` Indique que l’application a été redémarrée par le gestionnaire de redémarrage.

- `CCommandLineInfo::FileNothing` Désactive l’affichage d’une nouvelle fenêtre enfant MDI au démarrage. Par défaut, les applications MDI générées par l’Assistant Application affichent une nouvelle fenêtre enfant au démarrage. Pour désactiver cette fonctionnalité, une application peut utiliser `CCommandLineInfo::FileNothing` comme commande d’interpréteur de commandes lorsqu’elle appelle [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand` est appelé par le `InitInstance( )` de toutes les `CWinApp` classes dérivées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a> CCommandLineInfo :: m_strDriverName

Stocke la valeur du troisième paramètre sans indicateur sur la ligne de commande.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du pilote d’imprimante pour une commande imprimer sur Shell. L’implémentation par défaut de [ParseParam](#parseparam) définit ce membre de données uniquement si l' `/pt` indicateur a été trouvé sur la ligne de commande.

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a> CCommandLineInfo :: m_strFileName

Stocke la valeur du premier paramètre sans indicateur sur la ligne de commande.

```
CString m_strFileName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du fichier à ouvrir.

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a> CCommandLineInfo :: m_strPortName

Stocke la valeur du quatrième paramètre sans indicateur sur la ligne de commande.

```
CString m_strPortName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du port imprimante pour une commande imprimer sur Shell. L’implémentation par défaut de [ParseParam](#parseparam) définit ce membre de données uniquement si l' `/pt` indicateur a été trouvé sur la ligne de commande.

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a> CCommandLineInfo :: m_strPrinterName

Stocke la valeur du deuxième paramètre sans indicateur sur la ligne de commande.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom de l’imprimante pour une commande imprimer sur Shell. L’implémentation par défaut de [ParseParam](#parseparam) définit ce membre de données uniquement si l' `/pt` indicateur a été trouvé sur la ligne de commande.

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a> CCommandLineInfo :: m_strRestartIdentifier

Identificateur de redémarrage unique sur la ligne de commande.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Notes

L’identificateur de redémarrage est unique pour chaque instance de l’application.

Si le gestionnaire de redémarrage quitte l’application et qu’il est configuré pour le redémarrer, le gestionnaire de redémarrage exécute l’application à partir de la ligne de commande avec l’identificateur de redémarrage en tant que paramètre facultatif. Lorsque le gestionnaire de redémarrage utilise l’identificateur de redémarrage, l’application peut rouvrir les documents précédemment ouverts et récupérer les fichiers enregistrés de façon automatique.

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a> CCommandLineInfo ::P arseParam

L’infrastructure appelle cette fonction pour analyser/interpréter des paramètres individuels à partir de la ligne de commande. La deuxième version diffère de la première uniquement dans les projets Unicode.

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>Paramètres

*pszParam*<br/>
Paramètre ou indicateur.

*bFlag*<br/>
Indique si *pszParam* est un paramètre ou un indicateur.

*bLast*<br/>
Indique s’il s’agit du dernier paramètre ou indicateur sur la ligne de commande.

### <a name="remarks"></a>Notes

[CWinApp ::P arsecommandline](../../mfc/reference/cwinapp-class.md#parsecommandline) appelle `ParseParam` une fois pour chaque paramètre ou indicateur sur la ligne de commande, en passant l’argument à *pszParam*. Si le premier caractère du paramètre est un « **-** » ou un «» **/** , il est supprimé et *bFlag* a la valeur true. Lors de l’analyse du paramètre final, l' *explosion* est définie sur true.

L’implémentation par défaut de cette fonction reconnaît les indicateurs suivants : `/p` , `/pt` ,, `/dde` `/Automation` et `/Embedding` , comme indiqué dans le tableau suivant :

|Argument de ligne de commande|Commande exécutée|
|----------------------------|----------------------|
|*app*|Nouveau fichier.|
|nom de fichier de l' *application*|Ouvrez le fichier.|
|*application* `/p` extension|Imprimez le fichier sur l’imprimante par défaut.|
|*application* `/pt` nom du port du pilote d’imprimante|Imprimez le fichier sur l’imprimante spécifiée.|
|*application*`/dde`|Commande de démarrage et d’attente DDE.|
|*application*`/Automation`|Démarrez en tant que serveur OLE Automation.|
|*application*`/Embedding`|Démarrez pour modifier un élément OLE incorporé.|
|*application*`/Register`<br /><br /> *application*`/Regserver`|Indique à l’application d’effectuer toutes les tâches d’inscription.|
|*application*`/Unregister`<br /><br /> *application*`/Unregserver`|Indique à l’application d’effectuer toutes les tâches d’annulation de l’inscription.|

Ces informations sont stockées dans [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded)et [m_nShellCommand](#m_nshellcommand). Les indicateurs sont marqués par une barre oblique « **/** » ou un trait d’Union « **-** ».

L’implémentation par défaut place le premier paramètre sans indicateur dans [m_strFileName](#m_strfilename). Dans le cas de l' `/pt` indicateur, l’implémentation par défaut place les deuxième, troisième et quatrième paramètres sans indicateur dans [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername)et [m_strPortName](#m_strportname), respectivement.

L’implémentation par défaut affecte également à [m_bShowSplash](#m_bshowsplash) la valeur true uniquement dans le cas d’un nouveau fichier. Dans le cas d’un nouveau fichier, l’utilisateur a pris une mesure impliquant l’application elle-même. Dans tous les autres cas, y compris l’ouverture de fichiers existants à l’aide de l’interpréteur de commandes, l’action de l’utilisateur implique le fichier directement. Dans un point de vue centré sur les documents, l’écran de démarrage n’a pas besoin d’annoncer le démarrage de l’application.

Substituez cette fonction dans votre classe dérivée pour gérer d’autres valeurs d’indicateur et de paramètre.

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWinApp ::P arseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp ::P rocessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
