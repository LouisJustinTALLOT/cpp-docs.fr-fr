---
title: Ccommandlineinfo, classe
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
ms.openlocfilehash: 6e4b535da00fdcecf4ce52fad696cb5d2bc55efa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408145"
---
# <a name="ccommandlineinfo-class"></a>Ccommandlineinfo, classe

Contribue à l'analyse de la ligne de commande au démarrage de l'application.

## <a name="syntax"></a>Syntaxe

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Construit une valeur par défaut `CCommandLineInfo` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Remplacer ce rappel pour analyser des paramètres individuels.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Indique la ligne de commande `/Automation` option a été trouvée.|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Indique la ligne de commande `/Embedding` option a été trouvée.|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Indique si un écran de démarrage doit être indiqué.|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Indique la commande shell à traiter.|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Indique le pilote nom si la commande shell doit imprimer ; Sinon, elle est vide.|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Indique le nom de fichier à ouvrir ou à l’impression ; vide si la commande de l’interpréteur de commandes est nouveau ou DDE.|
|[CCommandLineInfo::m_strPortName](#m_strportname)|Indique le port nom si la commande shell doit imprimer ; Sinon, elle est vide.|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Indique l’imprimante nom si la commande shell doit imprimer ; Sinon, elle est vide.|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Indique l’identificateur unique de redémarrage pour le Gestionnaire de redémarrage, si le Gestionnaire de redémarrage redémarré l’application.|

## <a name="remarks"></a>Notes

Une application MFC crée généralement une instance locale de cette classe dans le [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) fonction de son objet d’application. Cet objet est ensuite passé à [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), qui appelle à plusieurs reprises [ParseParam](#parseparam) pour remplir le `CCommandLineInfo` objet. Le `CCommandLineInfo` objet est ensuite passé à [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) pour gérer les indicateurs et les arguments de ligne de commande.

Vous pouvez utiliser cet objet pour encapsuler les paramètres des options de ligne de commande suivantes :

|Argument de ligne de commande|Commande exécutée|
|----------------------------|----------------------|
|*app*|Nouveau fichier.|
|*application* nom de fichier|Ouvrir un fichier.|
|*application* `/p` nom de fichier|Imprimer le fichier à l’imprimante par défaut.|
|*application* `/pt` port de pilote d’imprimante nom de fichier|Imprimer le fichier à l’imprimante spécifiée.|
|*app* `/dde`|Démarrer et await commande DDE.|
|*app* `/Automation`|Démarrer comme serveur OLE automation.|
|*app* `/Embedding`|Démarrer modifier un élément OLE incorporé.|
|*app* `/Register`<br /><br /> *app* `/Regserver`|Informe l’application pour exécuter des tâches d’inscription.|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|Informe l’application pour exécuter des tâches de désinscription.|

Dérivez une nouvelle classe à partir de `CCommandLineInfo` pour gérer d’autres indicateurs et les valeurs de paramètre. Substituer [ParseParam](#parseparam) pour gérer les nouveaux indicateurs.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo

Ce constructeur crée un `CCommandLineInfo` objet avec les valeurs par défaut.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Notes

La valeur par défaut est de montrer l’écran de démarrage ( `m_bShowSplash=TRUE`) et pour exécuter la commande Nouveau dans le menu fichier ( `m_nShellCommand` **= NewFile**).

L’infrastructure d’application appelle [ParseParam](#parseparam) pour remplir les membres de données de cet objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated

Indique que le `/Automation` indicateur a été trouvé sur la ligne de commande.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, cela signifie démarrer comme serveur OLE automation.

##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded

Indique que le `/Embedding` indicateur a été trouvé sur la ligne de commande.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, cela signifie Démarrer pour la modification d’un élément OLE incorporé.

##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash

Indique que l’écran de démarrage doit être affiché.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, cela signifie que l’écran de démarrage pour cette application doit être affiché lors du démarrage. L’implémentation par défaut de [ParseParam](#parseparam) définit ce membre de données à la valeur TRUE si [m_nShellCommand](#m_nshellcommand) est égal à `CCommandLineInfo::FileNew`.

##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand

Indique la commande d’environnement pour cette instance de l’application.

```
m_nShellCommand;
```

### <a name="remarks"></a>Notes

Le type de ce membre de données est le type énuméré suivant, qui est défini dans le `CCommandLineInfo` classe.

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

- `CCommandLineInfo::FileNew` Indique qu’aucun nom de fichier a été trouvé sur la ligne de commande.

- `CCommandLineInfo::FileOpen` Indique qu’un nom de fichier a été trouvé sur la ligne de commande et qu’aucun des indicateurs suivants ont été trouvées sur la ligne de commande : `/p`, `/pt`, `/dde`.

- `CCommandLineInfo::FilePrint` Indique que le `/p` indicateur a été trouvé sur la ligne de commande.

- `CCommandLineInfo::FilePrintTo` Indique que le `/pt` indicateur a été trouvé sur la ligne de commande.

- `CCommandLineInfo::FileDDE` Indique que le `/dde` indicateur a été trouvé sur la ligne de commande.

- `CCommandLineInfo::AppRegister` Indique que le `/Register` ou `/Regserver` indicateur a été trouvé sur la ligne de commande et de l’application a été invitée à inscrire.

- `CCommandLineInfo::AppUnregister` Indique que le `/Unregister` ou `/Unregserver` application a été invitée à annuler l’inscription.

- `CCommandLineInfo::RestartByRestartManager` Indique que l’application a été redémarrée par le Gestionnaire de redémarrage.

- `CCommandLineInfo::FileNothing` Désactive l’affichage d’une nouvelle fenêtre d’enfants MDI au démarrage. Par conception, les applications MDI générées par l’Assistant de l’Application affichent une fenêtre enfant au démarrage. Pour désactiver cette fonctionnalité, une application peut utiliser `CCommandLineInfo::FileNothing` en tant que la commande shell lorsqu’il appelle [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand` est appelée par le `InitInstance( )` de tous les `CWinApp` classes dérivées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName

Stocke la valeur du troisième paramètre sans indicateur sur la ligne de commande.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du pilote d’imprimante pour une commande shell à imprimer. L’implémentation par défaut de [ParseParam](#parseparam) définit ce membre de données uniquement si le `/pt` indicateur a été trouvé sur la ligne de commande.

##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName

Stocke la valeur du premier paramètre sans indicateur sur la ligne de commande.

```
CString m_strFileName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du fichier à ouvrir.

##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName

Stocke la valeur du quatrième paramètre sans indicateur sur la ligne de commande.

```
CString m_strPortName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du port d’imprimante pour une commande shell à imprimer. L’implémentation par défaut de [ParseParam](#parseparam) définit ce membre de données uniquement si le `/pt` indicateur a été trouvé sur la ligne de commande.

##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName

Stocke la valeur du deuxième paramètre sans indicateur sur la ligne de commande.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom de l’imprimante pour une commande shell à imprimer. L’implémentation par défaut de [ParseParam](#parseparam) définit ce membre de données uniquement si le `/pt` indicateur a été trouvé sur la ligne de commande.

##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier

Vous redémarrez l’unique identificateur sur la ligne de commande.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Notes

Le redémarrage de l’identificateur est unique pour chaque instance de l’application.

Si le Gestionnaire de redémarrage quitte l’application et est configuré pour redémarrer, le Gestionnaire de redémarrage exécute l’application à partir de la ligne de commande avec l’identificateur de redémarrage comme un paramètre facultatif. Lorsque le Gestionnaire de redémarrage utilise l’identificateur de redémarrage, l’application peut rouvrir les documents précédemment ouverts et récupérer des fichiers d’enregistrée automatiquement.

##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam

L’infrastructure appelle cette fonction pour l’analyse/interpréter les paramètres individuels à partir de la ligne de commande. La deuxième version est différente de la première uniquement dans les projets d’Unicode.

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
Le paramètre ou un indicateur.

*bFlag*<br/>
Indique si *pszParam* est un paramètre ou un indicateur.

*bLast*<br/>
Indique si c’est le dernier paramètre ou indicateur sur la ligne de commande.

### <a name="remarks"></a>Notes

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) appels `ParseParam` qu’une seule fois pour chaque paramètre ou un indicateur sur la ligne de commande, en passant l’argument de *pszParam*. Si le premier caractère du paramètre est un « **-**'ou' **/** », il est supprimé et *bFlag* est définie sur TRUE. Lors de l’analyse le paramètre final, *bLast* est définie sur TRUE.

L’implémentation par défaut de cette fonction reconnaît les indicateurs suivants : `/p`, `/pt`, `/dde`, `/Automation`, et `/Embedding`, comme illustré dans le tableau suivant :

|Argument de ligne de commande|Commande exécutée|
|----------------------------|----------------------|
|*app*|Nouveau fichier.|
|*application* nom de fichier|Ouvrir un fichier.|
|*application* `/p` nom de fichier|Imprimer le fichier à l’imprimante par défaut.|
|*application* `/pt` port de pilote d’imprimante nom de fichier|Imprimer le fichier à l’imprimante spécifiée.|
|*app* `/dde`|Démarrer et await commande DDE.|
|*app* `/Automation`|Démarrer comme serveur OLE automation.|
|*app* `/Embedding`|Démarrer modifier un élément OLE incorporé.|
|*app* `/Register`<br /><br /> *app* `/Regserver`|Informe l’application pour exécuter des tâches d’inscription.|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|Informe l’application pour exécuter des tâches de désinscription.|

Ces informations sont stockées dans [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded), et [m_nShellCommand](#m_nshellcommand). Les indicateurs sont marquées par soit une barre oblique « **/**'ou un trait d’union' **-**».

L’implémentation par défaut place le premier paramètre sans indicateur dans [m_strFileName](#m_strfilename). Dans le cas de la `/pt` indicateur, l’implémentation par défaut place le deuxième, troisième et quatrième paramètres sans indicateur dans [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername), et [m_ strPortName](#m_strportname), respectivement.

L’implémentation par défaut définit également [m_bShowSplash](#m_bshowsplash) true uniquement dans le cas d’un nouveau fichier. Dans le cas d’un nouveau fichier, l’utilisateur a effectué les actions impliquant l’application elle-même. Dans tous les autres cas, y compris l’ouverture de fichiers existants à l’aide de l’interpréteur de commandes, l’action de l’utilisateur implique le fichier directement. Dans un point de vue centré sur les documents, l’écran de démarrage n’a pas besoin d’annoncer l’application démarre.

Remplacez cette fonction dans votre classe dérivée pour gérer les autres valeurs d’indicateur et des paramètres.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
