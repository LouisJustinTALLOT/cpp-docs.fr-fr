---
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
ms.openlocfilehash: 0b4d5e5d253f2eb10388a69286d21e2190826eba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369458"
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
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Construit un `CCommandLineInfo` objet par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Remplacer ce rappel pour analyser les paramètres individuels.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCommandLineInfo:m_bRunAutomated](#m_brunautomated)|Indique que l’option de ligne `/Automation` de commande a été trouvée.|
|[CCommandLineInfo:m_bRunEmbedded](#m_brunembedded)|Indique que l’option de ligne `/Embedding` de commande a été trouvée.|
|[CCommandLineInfo:m_bShowSplash](#m_bshowsplash)|Indique si un écran d’éclaboussure doit être affiché.|
|[CCommandLineInfo:m_nShellCommand](#m_nshellcommand)|Indique la commande de coquille à traiter.|
|[CCommandLineInfo:m_strDriverName](#m_strdrivername)|Indique le nom du conducteur si la commande de la coque est imprimée; autrement vide.|
|[CCommandLineInfo:m_strFileName](#m_strfilename)|Indique le nom du fichier à ouvrir ou à imprimer; vide si la commande de coquille est nouvelle ou DDE.|
|[CCommandLineInfo:m_strPortName](#m_strportname)|Indique le nom du port si la commande de la coque est imprimée; autrement vide.|
|[CCommandLineInfo:m_strPrinterName](#m_strprintername)|Indique le nom de l’imprimante si la commande de la coque est imprimée; autrement vide.|
|[CCommandLineInfo:m_strRestartIdentifier](#m_strrestartidentifier)|Indique l’identifiant de redémarrage unique pour le gestionnaire de redémarrage si le gestionnaire de redémarrage a redémarré l’application.|

## <a name="remarks"></a>Notes

Une application MFC créera généralement un exemple local de cette classe dans la fonction [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) de son objet d’application. Cet objet est ensuite transmis à [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), qui appelle à `CCommandLineInfo` plusieurs reprises [ParseParam](#parseparam) pour remplir l’objet. L’objet `CCommandLineInfo` est ensuite transmis à [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) pour gérer les arguments et les drapeaux de la ligne de commandement.

Vous pouvez utiliser cet objet pour encapsuler les options et paramètres suivants de la ligne de commande :

|Argument de ligne de commande|Commandement exécuté|
|----------------------------|----------------------|
|*app*|Nouveau fichier.|
|*nom* de fichier app|Fichier ouvert.|
|*nom* `/p` de fichier app|Imprimer le fichier à l’imprimante par défaut.|
|port de pilote d’imprimante de nom de fichier *d’application* `/pt`|Imprimer le fichier à l’imprimante spécifiée.|
|*application*`/dde`|Démarrez et attendez la commande DDE.|
|*application*`/Automation`|Démarrez comme un serveur d’automatisation OLE.|
|*application*`/Embedding`|Démarrez pour modifier un élément OLE intégré.|
|*application*`/Register`<br /><br /> *application*`/Regserver`|Informe l’application pour effectuer toutes les tâches d’inscription.|
|*application*`/Unregister`<br /><br /> *application*`/Unregserver`|Informe l’application d’effectuer des tâches de non-inscription.|

Dérivez une `CCommandLineInfo` nouvelle classe pour manipuler d’autres drapeaux et valeurs de paramètres. Remplacer [ParseParam](#parseparam) pour manipuler les nouveaux drapeaux.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a>CCommandLineInfo::CCommandLineInfo

Ce constructeur crée `CCommandLineInfo` un objet avec des valeurs par défaut.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Notes

La valeur par défaut est `m_bShowSplash=TRUE`d’afficher l’écran d’éclaboussure `m_nShellCommand`( ) et d’exécuter la nouvelle commande sur le menu Fichier ( **'NewFile**).

Le cadre d’application appelle [ParseParam](#parseparam) pour remplir les membres de données de cet objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a>CCommandLineInfo:m_bRunAutomated

Indique que `/Automation` le drapeau a été trouvé sur la ligne de commandement.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Notes

Si TRUE, cela signifie démarrer comme un serveur d’automatisation OLE.

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a>CCommandLineInfo:m_bRunEmbedded

Indique que `/Embedding` le drapeau a été trouvé sur la ligne de commandement.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Notes

Si TRUE, cela signifie démarrer pour l’édition d’un élément OLE intégré.

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a>CCommandLineInfo:m_bShowSplash

Indique que l’écran d’éclaboussure doit être affiché.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Notes

Si VRAI, cela signifie que l’écran d’éclaboussure pour cette application doit être affiché pendant le démarrage. La mise en œuvre par défaut de [ParseParam](#parseparam) définit `CCommandLineInfo::FileNew`ce membre des données à TRUE si [m_nShellCommand](#m_nshellcommand) est égal à .

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a>CCommandLineInfo:m_nShellCommand

Indique la commande de coquille pour le cas de l’application.

```
m_nShellCommand;
```

### <a name="remarks"></a>Notes

Le type pour ce membre de données est le type `CCommandLineInfo` énuméré suivant, qui est défini dans la classe.

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

Pour une brève description de ces valeurs, consultez la liste suivante.

- `CCommandLineInfo::FileNew`Indique qu’aucun nom de fichier n’a été trouvé sur la ligne de commande.

- `CCommandLineInfo::FileOpen`Indique qu’un nom de fichier a été trouvé sur la ligne de `/p` `/pt`commandement `/dde`et qu’aucun des drapeaux suivants n’a été trouvé sur la ligne de commandement : , . .

- `CCommandLineInfo::FilePrint`Indique que `/p` le drapeau a été trouvé sur la ligne de commandement.

- `CCommandLineInfo::FilePrintTo`Indique que `/pt` le drapeau a été trouvé sur la ligne de commandement.

- `CCommandLineInfo::FileDDE`Indique que `/dde` le drapeau a été trouvé sur la ligne de commandement.

- `CCommandLineInfo::AppRegister`Indique que `/Register` `/Regserver` le drapeau ou le drapeau a été trouvé sur la ligne de commandement et que la demande a été demandée de s’inscrire.

- `CCommandLineInfo::AppUnregister`Indique que `/Unregister` `/Unregserver` la demande ou la demande a été demandée de ne pas s’inscrire.

- `CCommandLineInfo::RestartByRestartManager`Indique que l’application a été redémarrée par le gestionnaire de redémarrage.

- `CCommandLineInfo::FileNothing`Éteigne l’affichage d’une nouvelle fenêtre pour enfants MDI sur le démarrage. Par conception, les applications MDI générées par Application Wizard affichent une nouvelle fenêtre enfant sur le démarrage. Pour désactiver cette fonctionnalité, une `CCommandLineInfo::FileNothing` application peut utiliser comme commande shell lorsqu’elle appelle [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand`est appelé `InitInstance( )` par `CWinApp` toutes les classes dérivées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a>CCommandLineInfo:m_strDriverName

Stocke la valeur du troisième paramètre non-drapeau sur la ligne de commande.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du pilote d’imprimante pour une commande d’impression à la coque. La mise en œuvre par défaut de `/pt` [ParseParam](#parseparam) ne définit ce membre des données que si le drapeau a été trouvé sur la ligne de commande.

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a>CCommandLineInfo:m_strFileName

Stocke la valeur du premier paramètre non-drapeau sur la ligne de commande.

```
CString m_strFileName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du fichier à ouvrir.

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a>CCommandLineInfo:m_strPortName

Stocke la valeur du quatrième paramètre non-drapeau sur la ligne de commande.

```
CString m_strPortName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom du port d’imprimante pour une commande d’impression à la coque. La mise en œuvre par défaut de `/pt` [ParseParam](#parseparam) ne définit ce membre des données que si le drapeau a été trouvé sur la ligne de commande.

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a>CCommandLineInfo:m_strPrinterName

Stocke la valeur du deuxième paramètre non-drapeau sur la ligne de commande.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Notes

Ce paramètre est généralement le nom de l’imprimante pour une commande d’impression à la coque. La mise en œuvre par défaut de `/pt` [ParseParam](#parseparam) ne définit ce membre des données que si le drapeau a été trouvé sur la ligne de commande.

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a>CCommandLineInfo:m_strRestartIdentifier

L’identifiant de redémarrage unique sur la ligne de commande.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Notes

L’identifiant de redémarrage est unique pour chaque cas de l’application.

Si le gestionnaire de redémarrage quitte l’application et est configuré pour la redémarrer, le gestionnaire de redémarrage exécute l’application à partir de la ligne de commande avec l’identifiant de redémarrage comme paramètre optionnel. Lorsque le gestionnaire de redémarrage utilise l’identifiant de redémarrage, l’application peut rouvrir les documents précédemment ouverts et récupérer les fichiers autosavés.

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a>CCommandLineInfo::ParseParam

Le cadre appelle cette fonction à analyser/interpréter les paramètres individuels de la ligne de commande. La deuxième version diffère de la première uniquement dans les projets Unicode.

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

*pszParam (pszParam)*<br/>
Le paramètre ou le drapeau.

*bFlag (en)*<br/>
Indique si *pszParam* est un paramètre ou un drapeau.

*Explosion*<br/>
Indique s’il s’agit du dernier paramètre ou drapeau sur la ligne de commande.

### <a name="remarks"></a>Notes

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) appelle `ParseParam` une fois pour chaque paramètre ou drapeau sur la ligne de commande, en passant l’argument à *pszParam*. Si le premier personnage du **-** paramètre est **/** un ' ou un ', alors il est enlevé et *bFlag* est réglé à VRAI. Lors de l’analyse du paramètre final, *bLast* est réglé sur TRUE.

La mise en œuvre par `/p` `/pt`défaut `/dde` `/Automation`de cette fonction reconnaît les indicateurs suivants: , , , et `/Embedding`, comme indiqué dans le tableau suivant:

|Argument de ligne de commande|Commandement exécuté|
|----------------------------|----------------------|
|*app*|Nouveau fichier.|
|*nom* de fichier app|Fichier ouvert.|
|*nom* `/p` de fichier app|Imprimer le fichier à l’imprimante par défaut.|
|port de pilote d’imprimante de nom de fichier *d’application* `/pt`|Imprimer le fichier à l’imprimante spécifiée.|
|*application*`/dde`|Démarrez et attendez la commande DDE.|
|*application*`/Automation`|Démarrez comme un serveur d’automatisation OLE.|
|*application*`/Embedding`|Démarrez pour modifier un élément OLE intégré.|
|*application*`/Register`<br /><br /> *application*`/Regserver`|Informe l’application pour effectuer toutes les tâches d’inscription.|
|*application*`/Unregister`<br /><br /> *application*`/Unregserver`|Informe l’application d’effectuer des tâches de non-inscription.|

Ces informations sont stockées dans [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded), et [m_nShellCommand](#m_nshellcommand). Les drapeaux sont marqués soit **/** par un **-** coup d’avance ' ou un trait d’union '..

La mise en œuvre par défaut met le premier paramètre non-drapeau dans [m_strFileName](#m_strfilename). Dans le cas `/pt` du drapeau, la mise en œuvre par défaut met les deuxième, troisième et quatrième paramètres non-drapeau dans [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername), et [m_strPortName](#m_strportname), respectivement.

La mise en œuvre par défaut ne définit également [m_bShowSplash](#m_bshowsplash) à TRUE que dans le cas d’un nouveau fichier. Dans le cas d’un nouveau fichier, l’utilisateur a pris des mesures impliquant l’application elle-même. Dans tous les autres cas, y compris l’ouverture de fichiers existants à l’aide de la coque, l’action utilisateur implique le fichier directement. Dans un point de vue centré sur le document, l’écran d’éclaboussure n’a pas besoin d’annoncer le démarrage de l’application.

Remplacer cette fonction dans votre classe dérivée pour gérer d’autres valeurs de drapeau et de paramètres.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
