---
title: Cusertoolsmanager, classe
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
ms.openlocfilehash: 857e86184e1b7ea399787520e9c4701547185133
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323370"
---
# <a name="cusertoolsmanager-class"></a>Cusertoolsmanager, classe

Gère la collection de [cusertool, classe](../../mfc/reference/cusertool-class.md) objets dans une application. Un outil utilisateur est un élément de menu qui exécute une application externe. L'objet `CUserToolsManager` permet à l'utilisateur ou au développeur d'ajouter de nouveaux outils utilisateur à l'application. Il prend en charge l'exécution des commandes associées aux outils utilisateur. En outre, il stocke des informations sur les outils utilisateur dans le Registre Windows.

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
|[CUserToolsManager::FindTool](#findtool)|Retourne le pointeur vers le `CMFCUserTool` objet qui est associé à un ID de commande spécifié.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Retourne l’ID de ressource qui est associé à la **Arguments** menu sur le **outils** onglet de la **personnaliser** boîte de dialogue.|
|[CUserToolsManager::GetDefExt](#getdefext)|Retourne l’extension par défaut qui le **ouvrir le fichier** boîte de dialogue ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) utilise dans le **commande** champ sur le **outils** onglet de la **Personnaliser** boîte de dialogue.|
|[CUserToolsManager::GetFilter](#getfilter)|Retourne le filtre de fichiers qui le **ouvrir le fichier** boîte de dialogue ( [classe CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le **commande** champ sur le **outils** onglet de la **Personnaliser** boîte de dialogue.|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Retourne l’ID de ressource qui est associé à la **répertoire Initial** menu sur le **outils** onglet de la **personnaliser** boîte de dialogue.|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Retourne le nombre maximal d’outils utilisateur qui peuvent être alloués dans l’application.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Retourne l’ID de commande de l’espace réservé d’élément menu pour les outils de l’utilisateur.|
|[CUserToolsManager::GetUserTools](#getusertools)|Retourne une référence à la liste des outils de l’utilisateur.|
|[CUserToolsManager::InvokeTool](#invoketool)|Exécute une application associée à l’outil utilisateur qui possède un ID de commande spécifiée.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Détermine si un ID de commande est associé à un outil utilisateur.|
|[CUserToolsManager::LoadState](#loadstate)|Charge des informations sur les outils de l’utilisateur à partir du Registre Windows.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Déplace l’outil utilisateur spécifié vers le bas dans la liste des outils de l’utilisateur.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Déplace vers le haut l’outil de l’utilisateur spécifié dans la liste des outils de l’utilisateur.|
|[CUserToolsManager::RemoveTool](#removetool)|Supprime l’outil de l’utilisateur spécifié à partir de l’application.|
|[CUserToolsManager::SaveState](#savestate)|Stocke des informations sur les outils de l’utilisateur dans le Registre Windows.|
|[CUserToolsManager::SetDefExt](#setdefext)|Spécifie l’extension par défaut qui le **ouvrir le fichier** boîte de dialogue ( [classe CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le **commande** champ sur le **outils** onglet de la **personnaliser** boîte de dialogue.|
|[CUserToolsManager::SetFilter](#setfilter)|Spécifie le fichier de filtre qui le **ouvrir le fichier** boîte de dialogue ( [classe CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le **commande** champ sur le **outils** onglet de la **Personnaliser** boîte de dialogue.|

## <a name="remarks"></a>Notes

Pour intégrer des outils de l’utilisateur dans votre application, vous devez :

1. Réserver un élément de menu et un ID de commande associée pour une entrée de menu outil utilisateur.

2. Réserver un ID de commande séquentiel de chaque outil utilisateur un utilisateur peut définir dans votre application.

3. Appelez le [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) méthode et fournir les paramètres suivants : menu ID de commande, premier ID de commande d’outil utilisateur et du dernier utilisateur ID commande d’outil.

Il doit y avoir qu’un seul global `CUserToolsManager` objet par application.

Pour obtenir un exemple d’outils de l’utilisateur, consultez l’exemple de projet VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer une référence à un `CUserToolsManager` objet et comment créer de nouveaux outils de l’utilisateur. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxusertoolsmanager.h

##  <a name="createnewtool"></a>  CUserToolsManager::CreateNewTool

Crée un nouvel outil utilisateur.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’outil de l’utilisateur nouvellement créé, ou NULL si le nombre d’outils de l’utilisateur a dépassé la valeur maximale. Le type retourné est le même que le type qui est passé à `CWinAppEx::EnableUserTools` en tant que le *pToolRTC* paramètre.

### <a name="remarks"></a>Notes

Cette méthode recherche le premier ID de commande de menu disponibles dans la plage qui est fournie dans l’appel à [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) et assigne l’outil utilisateur cet ID.

La méthode échoue si le nombre d’outils a atteint la valeur maximale. Cela se produit lorsque tous les ID de commande dans la plage sont affectés à des outils de l’utilisateur. Vous pouvez récupérer le nombre maximal d’outils en appelant [CUserToolsManager::GetMaxTools](#getmaxtools). Vous pouvez accéder à la liste des outils en appelant le [CUserToolsManager::GetUserTools](#getusertools) (méthode).

##  <a name="cusertoolsmanager"></a>  CUserToolsManager::CUserToolsManager

Construit un objet `CUserToolsManager`. Chaque application doit avoir au plus un responsable d’outils utilisateur.

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
[in] Entier non signé par le framework comme espace réservé pour l’ID de commande du menu outils utilisateur.

*uiCmdFirst*<br/>
[in] L’ID de commande pour la première commande d’outil utilisateur.

*uiCmdLast*<br/>
[in] L’ID de commande pour la dernière commande d’outil utilisateur.

*pToolRTC*<br/>
[in] La classe qui [CUserToolsManager::CreateNewTool](#createnewtool) crée. À l’aide de cette classe, vous pouvez utiliser un type dérivé de [cusertool, classe](../../mfc/reference/cusertool-class.md) au lieu de l’implémentation par défaut.

*uArgMenuID*<br/>
[in] L’ID de ressource de menu du menu contextuel arguments.

*uInitDirMenuID*<br/>
[in] L’ID de ressource de menu du menu contextuel répertoire initial.

### <a name="remarks"></a>Notes

N’appelez pas ce constructeur. Au lieu de cela, appelez [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils utilisateur, puis appelez [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) pour obtenir un pointeur vers le `CUserToolsManager`. Pour plus d’informations, consultez [outils définis par l’utilisateur](../../mfc/user-defined-tools.md).

##  <a name="findtool"></a>  CUserToolsManager::FindTool

Retourne le pointeur vers le [cusertool, classe](../../mfc/reference/cusertool-class.md) objet qui est associé à un ID de commande spécifié.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
[in] Un identificateur de commande de menu.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [cusertool, classe](../../mfc/reference/cusertool-class.md) ou `CUserTool`-objet dérivé si succès ; sinon, NULL.

### <a name="remarks"></a>Notes

Lorsque `FindTool` est réussie, le type retourné est le même que le type de la *pToolRTC* paramètre [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="getargumentsmenuid"></a>  CUserToolsManager::GetArgumentsMenuID

Retourne l’ID de ressource qui est associé à la **Arguments** menu sur le **outils** onglet de la **personnaliser** boîte de dialogue.

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Valeur de retour

L’identificateur d’une ressource de menu.

### <a name="remarks"></a>Notes

Le *uArgMenuID* paramètre de [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) Spécifie l’ID de la ressource.

##  <a name="getdefext"></a>  CUserToolsManager::GetDefExt

Retourne l’extension par défaut qui le **ouvrir le fichier** boîte de dialogue ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) utilise dans le **commande** champ sur le **outils** onglet de la **Personnaliser** boîte de dialogue.

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence à la `CString` objet qui contient l’extension.

##  <a name="getfilter"></a>  CUserToolsManager::GetFilter

Retourne le filtre de fichiers qui le **ouvrir le fichier** boîte de dialogue ( [classe CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le **commande** champ sur le **outils** onglet de la **Personnaliser** boîte de dialogue.

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence à la `CString` objet qui contient le filtre.

##  <a name="getinitialdirmenuid"></a>  CUserToolsManager::GetInitialDirMenuID

Retourne l’ID de ressource qui est associé à la **répertoire Initial** menu sur le **outils** onglet de la **personnaliser** boîte de dialogue.

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Valeur de retour

Identificateur de ressource de menu.

### <a name="remarks"></a>Notes

L’ID retourné est spécifié dans le *uInitDirMenuID* paramètre de [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="getmaxtools"></a>  CUserToolsManager::GetMaxTools

Retourne le nombre maximal d’outils utilisateur qui peuvent être alloués dans l’application.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximal d’outils utilisateur qui peuvent être alloués.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre maximal d’outils qui peuvent être alloués dans l’application. Ce nombre est le nombre d’ID dans la plage comprise entre le *uiCmdFirst* via la *uiCmdLast* les paramètres que vous passez à [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="gettoolsentrycmd"></a>  CUserToolsManager::GetToolsEntryCmd

Retourne l’ID de commande de l’espace réservé d’élément menu pour les outils de l’utilisateur.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Valeur de retour

L’ID de commande de l’espace réservé.

### <a name="remarks"></a>Notes

Pour activer les outils de l’utilisateur, vous appelez [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). Le *uiCmdToolsDummy* paramètre spécifie l’ID de la commande entrée outils. Cette méthode retourne l’ID de la commande d’entrée d’outils. Chaque fois que cet ID est utilisé dans un menu, elle est remplacée par la liste des outils de l’utilisateur lorsque le menu s’affiche.

##  <a name="getusertools"></a>  CUserToolsManager::GetUserTools

Retourne une référence à la liste des outils de l’utilisateur.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence const à un [CObList, classe](../../mfc/reference/coblist-class.md) objet qui contient une liste des outils de l’utilisateur.

### <a name="remarks"></a>Notes

Appel de cette méthode pour récupérer une liste de l’utilisateur des outils fournis par le [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) objet tient à jour. Chaque outil utilisateur est représenté par un objet de type [cusertool, classe](../../mfc/reference/cusertool-class.md) ou un type dérivé `CUserTool`. Le type est spécifié par le *pToolRTC* paramètre lorsque vous appelez [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils de l’utilisateur.

##  <a name="invoketool"></a>  CUserToolsManager::InvokeTool

Exécute une application associée à l’outil utilisateur qui possède un ID de commande spécifiée.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
[in] L’ID de commande de menu associé à l’outil utilisateur.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la commande associée à outil utilisateur a été exécutée avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Appel de cette méthode pour exécuter une application associée à l’utilisateur de l’outil qui a l’ID de commande spécifié par *uiCmdId*.

##  <a name="isusertoolcmd"></a>  CUserToolsManager::IsUserToolCmd

Détermine si un ID de commande est associé à un outil utilisateur.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
[in] ID de commande de l’élément de menu.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si un ID de commande donnée est associé à un outil utilisateur ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode vérifie si l’ID de commande donné est dans la plage d’ID de commande. Vous spécifiez la plage lorsque vous appelez [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils de l’utilisateur.

##  <a name="loadstate"></a>  CUserToolsManager::LoadState

Charge des informations sur les outils de l’utilisateur à partir du Registre Windows.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Le chemin d’accès de la clé de Registre Windows.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’état a été chargé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode charge l’état de la `CUserToolsManager` objet à partir du Registre Windows.

En règle générale, vous n’appelez pas cette méthode directement. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) appelle dans le cadre du processus de l’initialisation d’espace de travail.

##  <a name="movetooldown"></a>  CUserToolsManager::MoveToolDown

Déplace l’outil utilisateur spécifié vers le bas dans la liste des outils de l’utilisateur.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
[in] Spécifie l’outil de l’utilisateur à déplacer.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’outil de l’utilisateur a été déplacé vers le bas avec succès ; sinon 0.

### <a name="remarks"></a>Notes

La méthode échoue si l’outil qui le *pTool* Spécifie n’est pas dans la liste interne ou si l’outil est le dernier dans la liste.

##  <a name="movetoolup"></a>  CUserToolsManager::MoveToolUp

Déplace vers le haut l’outil de l’utilisateur spécifié dans la liste des outils de l’utilisateur.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
[in] Spécifie l’outil de l’utilisateur à déplacer.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’outil de l’utilisateur a été déplacé vers le haut avec succès ; sinon 0.

### <a name="remarks"></a>Notes

La méthode échoue si l’outil qui le *pTool* spécifie de paramètre n’est pas dans la liste interne ou si l’outil est le premier élément d’outil dans la liste.

##  <a name="removetool"></a>  CUserToolsManager::RemoveTool

Supprime l’outil de l’utilisateur spécifié à partir de l’application.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
[in, out] Pointeur vers un outil de l’utilisateur à supprimer.

### <a name="return-value"></a>Valeur de retour

TRUE si l’outil est supprimé avec succès. Sinon, FALSE.

### <a name="remarks"></a>Notes

Si l’outil est supprimé avec succès, cette méthode supprime *pTool*.

##  <a name="savestate"></a>  CUserToolsManager::SaveState

Stocke des informations sur les outils de l’utilisateur dans le Registre Windows.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Un chemin d’accès à la clé de Registre Windows.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’état a été enregistré avec succès ; sinon 0.

### <a name="remarks"></a>Notes

La méthode stocke l’état actuel de la `CUserToolsManager` objet dans le Registre Windows.

En règle générale, il est inutile d’appeler cette méthode directement, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) appelle automatiquement dans le cadre du processus de sérialisation d’espace de travail de l’application.

##  <a name="setdefext"></a>  CUserToolsManager::SetDefExt

Spécifie l’extension par défaut qui le **ouvrir le fichier** boîte de dialogue ( [classe CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le **commande** champ sur le **outils** onglet de la **personnaliser** boîte de dialogue.

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Paramètres

*strDefExt*<br/>
[in] Une chaîne de texte qui contient l’extension de nom de fichier par défaut.

### <a name="remarks"></a>Notes

Appelez cette méthode pour spécifier une extension de nom de fichier par défaut dans le **ouvrir le fichier** boîte de dialogue qui s’affiche lorsque l’utilisateur sélectionne une application à associer à l’outil utilisateur. La valeur par défaut est « exe ».

##  <a name="setfilter"></a>  CUserToolsManager::SetFilter

Spécifie le fichier de filtre qui le **ouvrir le fichier** boîte de dialogue ( [classe CFileDialog](../../mfc/reference/cfiledialog-class.md)) utilise dans le **commande** champ sur le **outils** onglet de la **Personnaliser** boîte de dialogue.

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Paramètres

*strFilter*<br/>
[in] Spécifie le filtre.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool, classe](../../mfc/reference/cusertool-class.md)
