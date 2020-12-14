---
description: 'En savoir plus sur : classe CUserToolsManager'
title: CUserToolsManager, classe
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
ms.openlocfilehash: 1c6b3b6ec2912a0093929ac117d878d54ed9757f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344950"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager, classe

Gère la collection d’objets de [classe CUserTool](../../mfc/reference/cusertool-class.md) dans une application. Un outil utilisateur est un élément de menu qui exécute une application externe. L'objet `CUserToolsManager` permet à l'utilisateur ou au développeur d'ajouter de nouveaux outils utilisateur à l'application. Il prend en charge l'exécution des commandes associées aux outils utilisateur. En outre, il stocke des informations sur les outils utilisateur dans le Registre Windows.

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
|[CUserToolsManager::FindTool](#findtool)|Retourne le pointeur vers l' `CMFCUserTool` objet associé à un ID de commande spécifié.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Retourne l’ID de ressource associé au menu **arguments** sous l’onglet **Outils** de la boîte de dialogue **personnaliser** .|
|[CUserToolsManager::GetDefExt](#getdefext)|Retourne l’extension par défaut utilisée par la boîte de dialogue d' **ouverture de fichier** ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) dans le champ **commande** de l’onglet **Outils** de la boîte de dialogue **personnaliser** .|
|[CUserToolsManager::GetFilter](#getfilter)|Retourne le filtre de fichiers que la boîte de dialogue d' **ouverture de fichier** ( [CFileDialog Class](../../mfc/reference/cfiledialog-class.md)) utilise dans le champ **commande** de l’onglet **Outils** de la boîte de dialogue **personnaliser** .|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Retourne l’ID de ressource associé au menu **initial Directory** sous l’onglet **Outils** de la boîte de dialogue **personnaliser** .|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Retourne le nombre maximal d’outils utilisateur qui peuvent être alloués dans l’application.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Retourne l’ID de commande de l’espace réservé d’élément de menu pour les outils utilisateur.|
|[CUserToolsManager::GetUserTools](#getusertools)|Retourne une référence à la liste des outils utilisateur.|
|[CUserToolsManager::InvokeTool](#invoketool)|Exécute une application associée à l’outil utilisateur qui a un ID de commande spécifié.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Détermine si un ID de commande est associé à un outil utilisateur.|
|[CUserToolsManager :: LoadState](#loadstate)|Charge des informations sur les outils utilisateur à partir du Registre Windows.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Déplace l’outil utilisateur spécifié vers le dessous de la liste des outils utilisateur.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Déplace l’outil utilisateur spécifié vers le haut de la liste des outils utilisateur.|
|[CUserToolsManager::RemoveTool](#removetool)|Supprime l’outil utilisateur spécifié de l’application.|
|[CUserToolsManager :: saveste](#savestate)|Stocke des informations sur les outils utilisateur dans le Registre Windows.|
|[CUserToolsManager::SetDefExt](#setdefext)|Spécifie l’extension par défaut utilisée par la boîte de dialogue d' **ouverture de fichier** ( [CFileDialog Class](../../mfc/reference/cfiledialog-class.md)) dans le champ **commande** de l’onglet **Outils** de la boîte de dialogue **personnaliser** .|
|[CUserToolsManager :: SetFilter](#setfilter)|Spécifie le filtre de fichiers utilisé par la boîte de dialogue d' **ouverture de fichier** ( [CFileDialog Class](../../mfc/reference/cfiledialog-class.md)) dans le champ **commande** de l’onglet **Outils** de la boîte de dialogue **personnaliser** .|

## <a name="remarks"></a>Notes

Pour incorporer les outils utilisateur dans votre application, vous devez :

1. Réservez un élément de menu et un ID de commande associé pour une entrée de menu d’outil utilisateur.

2. Réservez un ID de commande séquentiel pour chaque outil utilisateur qu’un utilisateur peut définir dans votre application.

3. Appelez la méthode [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) et fournissez les paramètres suivants : ID de commande de menu, ID de commande du premier outil utilisateur et ID de commande du dernier outil utilisateur.

Il ne doit y avoir qu’un seul `CUserToolsManager` objet global par application.

Pour obtenir un exemple d’outils utilisateur, consultez l’exemple de projet VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer une référence à un `CUserToolsManager` objet et comment créer de nouveaux outils utilisateur. Cet extrait de code fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Spécifications

**En-tête :** afxusertoolsmanager. h

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a> CUserToolsManager::CreateNewTool

Crée un nouvel outil utilisateur.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’outil utilisateur nouvellement créé, ou NULL si le nombre d’outils utilisateur a dépassé la valeur maximale. Le type retourné est le même que le type qui est passé à `CWinAppEx::EnableUserTools` en tant que paramètre *pToolRTC* .

### <a name="remarks"></a>Notes

Cette méthode recherche le premier ID de commande de menu disponible dans la plage fournie dans l’appel à [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) et affecte cet ID à l’outil utilisateur.

La méthode échoue si le nombre d’outils a atteint la valeur maximale. Cela se produit lorsque tous les ID de commande dans la plage sont affectés aux outils utilisateur. Vous pouvez récupérer le nombre maximal d’outils en appelant [CUserToolsManager :: GetMaxTools](#getmaxtools). Vous pouvez accéder à la liste des outils en appelant la méthode [CUserToolsManager :: GetUserTools](#getusertools) .

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a> CUserToolsManager::CUserToolsManager

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
dans Entier non signé que le Framework utilise comme espace réservé pour l’ID de commande du menu outils de l’utilisateur.

*uiCmdFirst*<br/>
dans ID de commande de la première commande de l’outil utilisateur.

*uiCmdLast*<br/>
dans ID de commande de la dernière commande de l’outil utilisateur.

*pToolRTC*<br/>
dans Classe que [CUserToolsManager :: CreateNewTool](#createnewtool) crée. En utilisant cette classe, vous pouvez utiliser un type dérivé de la [classe CUserTool](../../mfc/reference/cusertool-class.md) au lieu de l’implémentation par défaut.

*uArgMenuID*<br/>
dans ID de ressource de menu du menu contextuel d’arguments.

*uInitDirMenuID*<br/>
dans ID de ressource de menu du menu contextuel initial du répertoire.

### <a name="remarks"></a>Notes

N’appelez pas ce constructeur. Au lieu de cela, appelez [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils utilisateur et appelez [CWinAppEx :: GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) pour obtenir un pointeur vers le `CUserToolsManager` . Pour plus d’informations, consultez [Outils définis par l’utilisateur](../../mfc/user-defined-tools.md).

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a> CUserToolsManager::FindTool

Retourne le pointeur vers l’objet de [classe CUserTool](../../mfc/reference/cusertool-class.md) associé à un ID de commande spécifié.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
dans Identificateur de commande de menu.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une [classe CUserTool](../../mfc/reference/cusertool-class.md) ou un `CUserTool` objet dérivé de en cas de réussite ; sinon, null.

### <a name="remarks"></a>Notes

Lorsque `FindTool` réussit, le type retourné est le même que le type du paramètre *PToolRTC* pour [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a> CUserToolsManager::GetArgumentsMenuID

Retourne l’ID de ressource associé au menu **arguments** sous l’onglet **Outils** de la boîte de dialogue **personnaliser** .

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur d’une ressource de menu.

### <a name="remarks"></a>Notes

Le paramètre *uArgMenuID* de [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) spécifie l’ID de la ressource.

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a> CUserToolsManager::GetDefExt

Retourne l’extension par défaut utilisée par la boîte de dialogue d' **ouverture de fichier** ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) dans le champ **commande** de l’onglet **Outils** de la boîte de dialogue **personnaliser** .

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence à l' `CString` objet qui contient l’extension.

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a> CUserToolsManager::GetFilter

Retourne le filtre de fichiers que la boîte de dialogue d' **ouverture de fichier** ( [CFileDialog Class](../../mfc/reference/cfiledialog-class.md)) utilise dans le champ **commande** de l’onglet **Outils** de la boîte de dialogue **personnaliser** .

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence à l' `CString` objet qui contient le filtre.

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a> CUserToolsManager::GetInitialDirMenuID

Retourne l’ID de ressource associé au menu **initial Directory** sous l’onglet **Outils** de la boîte de dialogue **personnaliser** .

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur de ressource de menu.

### <a name="remarks"></a>Notes

L’ID retourné est spécifié dans le paramètre *uInitDirMenuID* de [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a> CUserToolsManager::GetMaxTools

Retourne le nombre maximal d’outils utilisateur qui peuvent être alloués dans l’application.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre maximal d’outils utilisateur qui peuvent être alloués.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre maximal d’outils pouvant être alloués dans l’application. Ce nombre correspond au nombre d’ID dans la plage de *uiCmdFirst* via les paramètres *uiCmdLast* que vous transmettez à [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a> CUserToolsManager::GetToolsEntryCmd

Retourne l’ID de commande de l’espace réservé d’élément de menu pour les outils utilisateur.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Valeur renvoyée

ID de commande de l’espace réservé.

### <a name="remarks"></a>Notes

Pour activer les outils utilisateur, vous devez appeler [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). Le paramètre *uiCmdToolsDummy* spécifie l’ID de commande de la commande d’entrée outils. Cette méthode retourne l’ID de commande de l’entrée outils. Chaque fois que cet ID est utilisé dans un menu, il est remplacé par la liste des outils utilisateur lorsque le menu s’affiche.

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a> CUserToolsManager::GetUserTools

Retourne une référence à la liste des outils utilisateur.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence const à un objet de [classe CObList](../../mfc/reference/coblist-class.md) qui contient une liste d’outils utilisateur.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer une liste d’outils utilisateur gérés par l’objet [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) . Chaque outil utilisateur est représenté par un objet de type [CUserTool](../../mfc/reference/cusertool-class.md) ou un type dérivé de `CUserTool` . Le type est spécifié par le paramètre *pToolRTC* lorsque vous appelez [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils utilisateur.

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a> CUserToolsManager::InvokeTool

Exécute une application associée à l’outil utilisateur qui a un ID de commande spécifié.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
dans ID de commande de menu associé à l’outil utilisateur.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la commande associée à l’outil utilisateur a été exécutée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette méthode pour exécuter une application associée à l’outil utilisateur avec l’ID de commande spécifié par *uiCmdId*.

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a> CUserToolsManager::IsUserToolCmd

Détermine si un ID de commande est associé à un outil utilisateur.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
dans ID de commande de l’élément de menu.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si un ID de commande donné est associé à un outil utilisateur ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode vérifie si l’ID de commande donné se trouve dans la plage d’ID de commande. Vous spécifiez la plage quand vous appelez [CWinAppEx :: EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils utilisateur.

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a> CUserToolsManager :: LoadState

Charge des informations sur les outils utilisateur à partir du Registre Windows.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Chemin d’accès de la clé de Registre Windows.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’État a été chargé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode charge l’état de l' `CUserToolsManager` objet à partir du Registre Windows.

En règle générale, vous n’appelez pas cette méthode directement. [CWinAppEx :: LoadState](../../mfc/reference/cwinappex-class.md#loadstate) l’appelle dans le cadre du processus d’initialisation de l’espace de travail.

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a> CUserToolsManager::MoveToolDown

Déplace l’outil utilisateur spécifié vers le dessous de la liste des outils utilisateur.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
dans Spécifie l’outil utilisateur à déplacer.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’outil utilisateur a été déplacé correctement ; Sinon, 0.

### <a name="remarks"></a>Notes

La méthode échoue si l’outil que le *pTool* spécifie ne figure pas dans la liste interne ou si l’outil est en dernier dans la liste.

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a> CUserToolsManager::MoveToolUp

Déplace l’outil utilisateur spécifié vers le haut de la liste des outils utilisateur.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
dans Spécifie l’outil utilisateur à déplacer.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’outil utilisateur a été déplacé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

La méthode échoue si l’outil que le paramètre *pTool* spécifie n’est pas dans la liste interne ou si l’outil est le premier élément de la liste.

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a> CUserToolsManager::RemoveTool

Supprime l’outil utilisateur spécifié de l’application.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Paramètres

*pTool*<br/>
[in, out] Pointeur vers un outil utilisateur à supprimer.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’outil est correctement supprimé. Dans le cas contraire, la valeur est FALSE.

### <a name="remarks"></a>Notes

Si l’outil est correctement supprimé, cette méthode supprime *pTool*.

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a> CUserToolsManager :: saveste

Stocke des informations sur les outils utilisateur dans le Registre Windows.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Chemin d’accès à la clé de Registre Windows.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’État a été enregistré avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

La méthode stocke l’état actuel de l' `CUserToolsManager` objet dans le Registre Windows.

En règle générale, vous n’avez pas besoin d’appeler cette méthode directement, [CWinAppEx :: Pro](../../mfc/reference/cwinappex-class.md#savestate) l’appelle automatiquement dans le cadre du processus de sérialisation de l’espace de travail de l’application.

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a> CUserToolsManager::SetDefExt

Spécifie l’extension par défaut utilisée par la boîte de dialogue d' **ouverture de fichier** ( [CFileDialog Class](../../mfc/reference/cfiledialog-class.md)) dans le champ **commande** de l’onglet **Outils** de la boîte de dialogue **personnaliser** .

```cpp
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Paramètres

*strDefExt*<br/>
dans Chaîne de texte qui contient l’extension de nom de fichier par défaut.

### <a name="remarks"></a>Notes

Appelez cette méthode pour spécifier une extension de nom de fichier par défaut dans la boîte de dialogue **ouvrir un fichier** , qui s’affiche lorsque l’utilisateur sélectionne une application à associer à l’outil utilisateur. La valeur par défaut est « exe ».

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a> CUserToolsManager :: SetFilter

Spécifie le filtre de fichiers utilisé par la boîte de dialogue d' **ouverture de fichier** ( [CFileDialog Class](../../mfc/reference/cfiledialog-class.md)) dans le champ **commande** de l’onglet **Outils** de la boîte de dialogue **personnaliser** .

```cpp
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Paramètres

*strFilter*<br/>
dans Spécifie le filtre.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool, classe](../../mfc/reference/cusertool-class.md)
