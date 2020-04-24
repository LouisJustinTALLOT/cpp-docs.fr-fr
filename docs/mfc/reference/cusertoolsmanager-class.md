---
title: Classe CUserToolsManager
ms.date: 11/04/2016
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
ms.openlocfilehash: 1e9be5d7cb81f2769b98d9baeae786873f5fa73d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751983"
---
# <a name="cusertoolsmanager-class"></a>Classe CUserToolsManager

Maintient la collection d’objets de [classe CUserTool](../../mfc/reference/cusertool-class.md) dans une application. Un outil utilisateur est un élément de menu qui exécute une application externe. L'objet `CUserToolsManager` permet à l'utilisateur ou au développeur d'ajouter de nouveaux outils utilisateur à l'application. Il prend en charge l'exécution des commandes associées aux outils utilisateur. En outre, il stocke des informations sur les outils utilisateur dans le Registre Windows.

## <a name="syntax"></a>Syntaxe

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|Construit un objet `CUserToolsManager`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CUserToolsManager::CreateNewTool](#createnewtool)|Crée un nouvel outil utilisateur.|
|[CUserToolsManager::FindTool](#findtool)|Renvoie le `CMFCUserTool` pointeur à l’objet associé à une pièce d’identité de commande spécifiée.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Retourne l’ID de ressource associé au menu **Arguments** sur l’onglet **Outils** de la boîte de dialogue **Customize.**|
|[CUserToolsManager::GetDefExt](#getdefext)|Retourne l’extension par défaut que la boîte de dialogue **De File Open** ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) utilise dans le champ **de commande** sur l’onglet **Outils** de la boîte de dialogue **Customize.**|
|[CUserToolsManager::GetFilter](#getfilter)|Retourne le filtre de fichier que la boîte de dialogue **De File Open** ( Classe [CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le champ **de commande** sur l’onglet **Outils** de la boîte de dialogue **Customize.**|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Retourne l’ID de ressource associé au menu initial de **l’annuaire** sur l’onglet **Outils** de la boîte de dialogue **Customize.**|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Retourne le nombre maximum d’outils utilisateur qui peuvent être alloués dans l’application.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Retourne l’ID de commande du placeholder de l’élément de menu pour les outils utilisateur.|
|[CUserToolsManager::GetUserTools](#getusertools)|Renvoie une référence à la liste des outils utilisateur.|
|[CUserToolsManager::InvokeTool](#invoketool)|Exécute une application associée à l’outil utilisateur qui dispose d’un IDENTIFIANT de commande spécifié.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Détermine si un IDENTIFIANT de commande est associé à un outil utilisateur.|
|[CUserToolsManager::LoadState](#loadstate)|Charge les informations sur les outils utilisateur du registre Windows.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Déplace l’outil utilisateur spécifié dans la liste des outils utilisateur.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Déplace l’outil utilisateur spécifié dans la liste des outils utilisateur.|
|[CUserToolsManager::RemoveTool](#removetool)|Supprime l’outil utilisateur spécifié de l’application.|
|[CUserToolsManager::SaveState](#savestate)|Stocke des informations sur les outils utilisateur dans le registre Windows.|
|[CUserToolsManager::SetDefExt](#setdefext)|Spécifie l’extension par défaut que la boîte de dialogue **De File Open** ( Classe [CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le champ **de commande** sur l’onglet **Outils** de la boîte de dialogue **Customize.**|
|[CUserToolsManager::SetFilter](#setfilter)|Spécifie le filtre de fichier que la boîte de dialogue **De File Open** ( Classe [CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le champ **de commande** sur l’onglet **Outils** de la boîte de dialogue **Customize.**|

## <a name="remarks"></a>Notes

Pour intégrer des outils utilisateur dans votre application, vous devez :

1. Réservez un élément de menu et un identifiant de commande associé pour une entrée de menu d’outil utilisateur.

2. Réservez un identifiant de commande séquentiel pour chaque outil utilisateur qu’un utilisateur peut définir dans votre application.

3. Appelez la méthode [CWinAppEx: ::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) et fournissez les paramètres suivants : ID de commande de menu, premier ID de commande d’outil utilisateur, et dernier IDENTIFIANT de commande d’outil utilisateur.

Il ne devrait `CUserToolsManager` y avoir qu’un seul objet global par application.

Pour un exemple d’outils utilisateur, consultez le projet d’exemple VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer `CUserToolsManager` une référence à un objet et comment créer de nouveaux outils d’utilisateur. Cet extrait de code fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Spécifications

**En-tête:** afxusertoolsmanager.h

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a>CUserToolsManager::CreateNewTool

Crée un nouvel outil utilisateur.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’outil utilisateur nouvellement créé, ou NULL si le nombre d’outils utilisateur a dépassé le maximum. Le type retourné est le même que `CWinAppEx::EnableUserTools` le type qui est transmis comme le paramètre *pToolRTC.*

### <a name="remarks"></a>Notes

Cette méthode trouve le premier ID de commande de menu disponible dans la gamme qui est fournie dans l’appel à [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) et assigne l’outil utilisateur de cet ID.

La méthode échoue si le nombre d’outils a atteint le maximum. Cela se produit lorsque toutes les identifiants de commande dans la plage sont affectés à des outils utilisateur. Vous pouvez récupérer le nombre maximum d’outils en appelant [CUserToolsManager:GetMaxTools](#getmaxtools). Vous pouvez accéder à la liste des outils en appelant la méthode [CUserToolsManager:GetUserTools](#getusertools) méthode.

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager

Construit un objet `CUserToolsManager`. Chaque application doit avoir au plus un gestionnaire d’outils utilisateur.

```
CUserToolsManager();

CUserToolsManager(
    const UINT uiCmdToolsDummy,
    const UINT uiCmdFirst,
    const UINT uiCmdLast,
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),
    UINT uArgMenuID=0,
    UINT uInitDirMenuID=0);
```

### <a name="parameters"></a>Paramètres

*uiCmdToolsDummy*<br/>
[dans] Un insignable que le cadre utilise comme un espace réservé pour l’ID de commande du menu des outils utilisateur.

*uiCmdFirst*<br/>
[dans] L’ID de commande pour la première commande d’outil utilisateur.

*uiCmdLast*<br/>
[dans] L’ID de commande pour la dernière commande d’outil utilisateur.

*pToolRTC (en)*<br/>
[dans] La classe celui [CUserToolsManager::CreateNewTool](#createnewtool) crée. En utilisant cette classe, vous pouvez utiliser un type dérivé de [classe CUserTool](../../mfc/reference/cusertool-class.md) au lieu de l’implémentation par défaut.

*uArgMenuID*<br/>
[dans] L’ID de ressource de menu du menu popup arguments.

*uInitDirMenuID*<br/>
[dans] L’ID de ressource de menu du menu popup de répertoire initial.

### <a name="remarks"></a>Notes

N’appelez pas ce constructeur. Au lieu de cela, appelez [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils utilisateur, et appelez [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) pour obtenir un pointeur à la `CUserToolsManager`. Pour plus d’informations, voir [Outils définis par l’utilisateur](../../mfc/user-defined-tools.md).

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a>CUserToolsManager::FindTool

Renvoie le pointeur à l’objet [de classe CUserTool](../../mfc/reference/cusertool-class.md) qui est associé à une pièce d’identité de commande spécifiée.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
[dans] Un identifiant de commande de menu.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une classe `CUserTool` [CUserTool](../../mfc/reference/cusertool-class.md) ou un objet dérivé en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Lorsqu’il `FindTool` est réussi, le type retourné est le même que le type de paramètre *pToolRTC* à [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID

Retourne l’ID de ressource associé au menu **Arguments** sur l’onglet **Outils** de la boîte de dialogue **Customize.**

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Valeur de retour

L’identifiant d’une ressource de menu.

### <a name="remarks"></a>Notes

Le paramètre *uArgMenuID* de [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) spécifie l’ID de la ressource.

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a>CUserToolsManager::GetDefExt

Retourne l’extension par défaut que la boîte de dialogue **De File Open** ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) utilise dans le champ **de commande** sur l’onglet **Outils** de la boîte de dialogue **Customize.**

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence `CString` à l’objet qui contient l’extension.

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a>CUserToolsManager::GetFilter

Retourne le filtre de fichier que la boîte de dialogue **De File Open** ( Classe [CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le champ **de commande** sur l’onglet **Outils** de la boîte de dialogue **Customize.**

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence `CString` à l’objet qui contient le filtre.

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID

Retourne l’ID de ressource associé au menu initial de **l’annuaire** sur l’onglet **Outils** de la boîte de dialogue **Customize.**

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Valeur de retour

Un identificateur de ressources de menu.

### <a name="remarks"></a>Notes

L’ID retourné est spécifié dans le *paramètre uInitDirMenuID* de [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a>CUserToolsManager::GetMaxTools

Retourne le nombre maximum d’outils utilisateur qui peuvent être alloués dans l’application.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximum d’outils utilisateur qui peuvent être alloués.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre maximum d’outils qui peuvent être alloués dans l’application. Ce nombre est le nombre d’IDs dans la gamme de *l’uiCmdFirst* à travers les paramètres *uiCmdLast* que vous passez à [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd

Retourne l’ID de commande du placeholder de l’élément de menu pour les outils utilisateur.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Valeur de retour

La carte d’identité du placeholder.

### <a name="remarks"></a>Notes

Pour activer les outils utilisateur, vous appelez [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). Le paramètre *uiCmdToolsDummy* spécifie l’ID de commande de la commande d’entrée des outils. Cette méthode renvoie l’ID de commande d’entrée des outils. Partout où cette pièce d’identité est utilisée dans un menu, elle est remplacée par la liste des outils utilisateur lorsque le menu apparaît.

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a>CUserToolsManager::GetUserTools

Renvoie une référence à la liste des outils utilisateur.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence const à un objet [CObList Class](../../mfc/reference/coblist-class.md) qui contient une liste d’outils utilisateur.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer une liste d’outils utilisateur que l’objet [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) maintient. Chaque outil utilisateur est représenté par un objet de type classe `CUserTool` [CUserTool](../../mfc/reference/cusertool-class.md) ou un type dérivé de . Le type est spécifié par le *paramètre pToolRTC* lorsque vous appelez [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils utilisateur.

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a>CUserToolsManager::InvokeTool

Exécute une application associée à l’outil utilisateur qui dispose d’un IDENTIFIANT de commande spécifié.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
[dans] L’ID de commande du menu associé à l’outil utilisateur.

### <a name="return-value"></a>Valeur de retour

Nonzero si la commande associée à l’outil utilisateur a été exécutée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette méthode pour exécuter une application associée à l’outil utilisateur qui a l’ID de commande spécifié par *uiCmdId*.

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd

Détermine si un IDENTIFIANT de commande est associé à un outil utilisateur.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
[dans] Une pièce d’identité de commande de l’élément de menu.

### <a name="return-value"></a>Valeur de retour

Nonzero si un ID de commande donné est associé à un outil utilisateur; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode vérifie si l’ID de commande donné se trouve dans la plage d’identification de commande. Vous spécifiez la plage lorsque vous appelez [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils utilisateur.

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a>CUserToolsManager::LoadState

Charge les informations sur les outils utilisateur du registre Windows.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Le chemin de la clé de registre Windows.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’État a été chargé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode charge l’état de l’objet `CUserToolsManager` à partir du registre Windows.

Habituellement, vous n’appelez pas cette méthode directement. [CWinAppEx::LoadState l’appelle](../../mfc/reference/cwinappex-class.md#loadstate) dans le cadre du processus d’initialisation de l’espace de travail.

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a>CUserToolsManager::MoveToolDown

Déplace l’outil utilisateur spécifié dans la liste des outils utilisateur.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
[dans] Spécifie l’outil utilisateur pour se déplacer.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’outil utilisateur a été déplacé vers le bas avec succès; sinon 0.

### <a name="remarks"></a>Notes

La méthode échoue si l’outil que le *pTool* spécifie n’est pas dans la liste interne ou si l’outil est le dernier dans la liste.

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a>CUserToolsManager::MoveToolUp

Déplace l’outil utilisateur spécifié dans la liste des outils utilisateur.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
[dans] Spécifie l’outil utilisateur pour se déplacer.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’outil utilisateur a été déplacé vers le haut avec succès ; sinon 0.

### <a name="remarks"></a>Notes

La méthode échoue si l’outil que le paramètre *pTool* spécifie n’est pas dans la liste interne ou si l’outil est le premier élément d’outil dans la liste.

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a>CUserToolsManager::RemoveTool

Supprime l’outil utilisateur spécifié de l’application.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
[dans, dehors] Un pointeur vers un outil utilisateur à supprimer.

### <a name="return-value"></a>Valeur de retour

VRAI si l’outil est supprimé avec succès. Dans le cas contraire, la valeur est FALSE.

### <a name="remarks"></a>Notes

Si l’outil est supprimé avec succès, cette méthode supprime *pTool*.

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a>CUserToolsManager::SaveState

Stocke des informations sur les outils utilisateur dans le registre Windows.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Un chemin vers la clé du registre Windows.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’État a été sauvé avec succès; sinon 0.

### <a name="remarks"></a>Notes

La méthode stocke l’état actuel de l’objet `CUserToolsManager` dans le registre Windows.

Habituellement, vous n’avez pas besoin d’appeler cette méthode directement, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) l’appelle automatiquement dans le cadre du processus de sérialisation de l’espace de travail de l’application.

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a>CUserToolsManager::SetDefExt

Spécifie l’extension par défaut que la boîte de dialogue **De File Open** ( Classe [CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le champ **de commande** sur l’onglet **Outils** de la boîte de dialogue **Customize.**

```cpp
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Paramètres

*strDefExt*<br/>
[dans] Une chaîne de texte qui contient l’extension du nom de fichier par défaut.

### <a name="remarks"></a>Notes

Appelez cette méthode pour spécifier une extension de nom de fichier par défaut dans la boîte de dialogue **De Fichier Open,** qui s’affiche lorsque l’utilisateur sélectionne une application pour s’associer à l’outil utilisateur. La valeur par défaut est "exe".

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a>CUserToolsManager::SetFilter

Spécifie le filtre de fichier que la boîte de dialogue **De File Open** ( Classe [CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le champ **de commande** sur l’onglet **Outils** de la boîte de dialogue **Customize.**

```cpp
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Paramètres

*strFilter (strFilter)*<br/>
[dans] Spécifie le filtre.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool, classe](../../mfc/reference/cusertool-class.md)
