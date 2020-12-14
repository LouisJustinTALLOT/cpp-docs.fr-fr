---
description: 'En savoir plus sur : classe CContextMenuManager'
title: CContextMenuManager, classe
ms.date: 11/04/2016
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
ms.openlocfilehash: f026b493ae5f7ae90eccc416d8920d8b699e975d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227817"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager, classe

L' `CContextMenuManager` objet gère les menus contextuels, également appelés menus contextuels.

## <a name="syntax"></a>Syntaxe

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Construit un objet `CContextMenuManager`.|
|`CContextMenuManager::~CContextMenuManager`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CContextMenuManager :: AjouterMenu](#addmenu)|Ajoute un nouveau menu contextuel.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Retourne un handle au menu associé à l’ID de ressource fourni.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Retourne un handle au menu qui correspond au nom de menu fourni.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Retourne une liste de noms de menu.|
|[CContextMenuManager :: LoadState](#loadstate)|Charge les menus contextuels stockés dans le Registre Windows.|
|[CContextMenuManager :: ResetState](#resetstate)|Efface les menus contextuels du gestionnaire de menus contextuels.|
|[CContextMenuManager :: saveste](#savestate)|Enregistre les menus contextuels dans le Registre Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Contrôle si `CContextMenuManager` ferme le menu contextuel actif lorsqu’il affiche un nouveau menu contextuel.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Affiche le menu contextuel spécifié.|
|[CContextMenuManager :: TrackPopupMenu](#trackpopupmenu)|Affiche le menu contextuel spécifié. Retourne l’index de la commande de menu sélectionnée.|

## <a name="remarks"></a>Notes

`CContextMenuManager` gère les menus contextuels et s’assure qu’ils ont une apparence cohérente.

Vous ne devez pas créer un `CContextMenuManager` objet manuellement. L’infrastructure de votre application crée l' `CContextMenuManager` objet. Toutefois, vous devez appeler [CWinAppEx :: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) lorsque votre application est initialisée. Après l’initialisation du gestionnaire de contexte, utilisez la méthode [CWinAppEx :: GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) pour obtenir un pointeur vers le gestionnaire de contexte de votre application.

Vous pouvez créer des menus contextuels au moment de l’exécution en appelant `AddMenu` . Si vous souhaitez afficher le menu sans recevoir d’abord l’entrée d’utilisateur, appelez `ShowPopupMenu` . `TrackPopupMenu` est utilisé lorsque vous souhaitez créer un menu et attendre une entrée utilisateur. `TrackPopupMenu` retourne l’index de la commande sélectionnée ou 0 si l’utilisateur s’est fermé sans sélectionner quoi que ce soit.

`CContextMenuManager`Peut également enregistrer et charger son état dans le Registre Windows.

## <a name="example"></a>Exemple

L’exemple suivant montre comment ajouter un menu à un `CContextMenuManager` objet et comment ne pas fermer le menu contextuel actif lorsque l' `CContextMenuManager` objet affiche un nouveau menu contextuel. Cet extrait de code fait partie de l' [exemple de pages personnalisées](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcontextmenumanager. h

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a> CContextMenuManager :: AjouterMenu

Ajoute un nouveau menu contextuel au [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>Paramètres

*uiMenuNameResId*<br/>
dans ID de ressource pour une chaîne qui contient le nom du nouveau menu.

*uiMenuResId*<br/>
dans ID de ressource de menu.

*lpszName*<br/>
dans Chaîne qui contient le nom du nouveau menu.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la méthode a réussi ; 0 si la méthode échoue.

### <a name="remarks"></a>Notes

Cette méthode échoue si *uiMenuResId* n’est pas valide ou si un autre menu portant le même nom se trouve déjà dans `CContextMenuManager` .

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a> CContextMenuManager::CContextMenuManager

Construit un objet [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) .

```
CContextMenuManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous ne devez pas créer un `CContextMenuManager` manuellement. L’infrastructure de votre application crée l' `CContextMenuManager` objet. Vous devez appeler [CWinAppEx :: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) pendant l’initialisation de votre application. Pour obtenir un pointeur vers le gestionnaire de contexte, appelez [CWinAppEx :: GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a> CContextMenuManager::GetMenuById

Retourne un handle au menu associé à un ID de ressource donné.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Paramètres

*nMenuResId*<br/>
dans ID de ressource pour le menu.

### <a name="return-value"></a>Valeur renvoyée

Handle vers le menu associé ou `NULL` si le menu est introuvable.

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a> CContextMenuManager::GetMenuByName

Retourne un handle vers un menu spécifique.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
dans Chaîne qui contient le nom du menu à récupérer.

*puiOrigResID*<br/>
à Pointeur vers un UINT. Ce paramètre contient l’ID de ressource du menu spécifié, s’il est trouvé.

### <a name="return-value"></a>Valeur renvoyée

Handle vers le menu qui correspond au nom spécifié par *lpszName*. NULL s’il n’y a aucun menu appelé *lpszName*.

### <a name="remarks"></a>Notes

Si cette méthode trouve un menu qui correspond à *lpszName*, `GetMenuByName` stocke l’ID de ressource de menu dans le paramètre *puiOrigResID*.

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a> CContextMenuManager::GetMenuNames

Retourne la liste des noms de menu ajoutés au [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```cpp
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Paramètres

*listOfNames*<br/>
à Référence à un paramètre [CStringList](../../mfc/reference/cstringlist-class.md) . Cette méthode écrit la liste des noms de menu dans ce paramètre.

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a> CContextMenuManager :: LoadState

Charge les informations associées à la [classe CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) à partir du Registre Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Chaîne qui contient le chemin d’accès relatif d’une clé de registre.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la méthode réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

Le paramètre *lpszProfileName* n’est pas le chemin d’accès absolu d’une entrée de registre. Il s’agit d’un chemin d’accès relatif qui est ajouté à la fin de la clé de Registre par défaut pour votre application. Pour récupérer ou définir la clé de Registre par défaut, utilisez respectivement les méthodes [CWinAppEx :: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) et [CWinAppEx :: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) .

Utilisez la méthode [CContextMenuManager :: saveste](#savestate) pour enregistrer les menus contextuels dans le registre.

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a> CContextMenuManager :: ResetState

Efface tous les éléments des menus contextuels associés à la [classe CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode réussit ; FALSe si une défaillance se produit.

### <a name="remarks"></a>Notes

Cette méthode efface les menus contextuels et les supprime de `CContextMenuManager` .

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a> CContextMenuManager :: saveste

Enregistre les informations associées à la [classe CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) dans le Registre Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Chaîne qui contient le chemin d’accès relatif d’une clé de registre.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la méthode réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

Le paramètre *lpszProfileName* n’est pas le chemin d’accès absolu d’une entrée de registre. Il s’agit d’un chemin d’accès relatif qui est ajouté à la fin de la clé de Registre par défaut pour votre application. Pour récupérer ou définir la clé de Registre par défaut, utilisez respectivement les méthodes [CWinAppEx :: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) et [CWinAppEx :: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) .

Utilisez la méthode [CContextMenuManager :: LoadState](#loadstate) pour charger les menus contextuels à partir du Registre.

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a> CContextMenuManager::SetDontCloseActiveMenu

Contrôle si le [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) ferme le menu contextuel actif lorsqu’il affiche un nouveau menu contextuel.

```cpp
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSet*<br/>
dans Paramètre booléen qui contrôle s’il faut fermer le menu contextuel actif. La valeur TRUE indique que le menu contextuel actif n’est pas fermé. La valeur FALSe indique que le menu contextuel actif est fermé.

### <a name="remarks"></a>Notes

Par défaut, le `CContextMenuManager` ferme le menu contextuel actif.

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a> CContextMenuManager::ShowPopupMenu

Affiche le menu contextuel spécifié.

```
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bRightAlign = FALSE);

virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bAutoDestroy = TRUE,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Paramètres

*uiMenuResId*<br/>
dans ID de ressource du menu affiché par cette méthode.

*x*<br/>
dans Décalage horizontal du menu contextuel dans les coordonnées clientes.

*y*<br/>
dans Décalage vertical du menu contextuel dans les coordonnées clientes

*pWndOwner*<br/>
dans Pointeur vers la fenêtre parente du menu contextuel.

*bOwnMessage*<br/>
dans Paramètre booléen qui indique comment les messages sont routés. Si *bOwnMessage* a la valeur false, le routage MFC standard est utilisé. Dans le cas contraire, *pWndOwner* reçoit les messages.

*hmenuPopup*<br/>
dans Handle du menu affiché par cette méthode.

*bAutoDestroy*<br/>
dans Paramètre booléen qui indique si le menu sera automatiquement détruit.

*bRightAlign*<br/>
dans Paramètre booléen qui indique comment les éléments de menu sont alignés. Si *bRightAlign* a la valeur true, le menu est aligné à droite pour l’ordre de lecture de droite à gauche.

### <a name="return-value"></a>Valeur renvoyée

La première surcharge de méthode retourne une valeur différente de zéro si la méthode affiche le menu avec succès ; Sinon, 0. La deuxième surcharge de méthode retourne un pointeur vers [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) si le menu contextuel s’affiche correctement ; Sinon, NULL.

### <a name="remarks"></a>Notes

Cette méthode ressemble à la méthode [CContextMenuManager :: TrackPopupMenu](#trackpopupmenu) dans le sens où les deux méthodes affichent un menu contextuel. Toutefois, `TrackPopupMenu` retourne l’index de la commande de menu sélectionnée.

Si le paramètre *bAutoDestroy* a la valeur false, vous devez appeler manuellement la méthode héritée `DestroyMenu` pour libérer des ressources mémoire. L’implémentation par défaut de `ShowPopupMenu` n’utilise pas le paramètre *bAutoDestroy*. Il est fourni pour une utilisation ultérieure ou pour les classes personnalisées dérivées de la `CContextMenuManager` classe.

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a> CContextMenuManager :: TrackPopupMenu

Affiche le menu contextuel spécifié et retourne l’index de la commande de menu contextuel sélectionnée.

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Paramètres

*hmenuPopup*<br/>
dans Handle du menu contextuel affiché par cette méthode.

*x*<br/>
dans Décalage horizontal du menu contextuel dans les coordonnées clientes.

*y*<br/>
dans Décalage vertical du menu contextuel dans les coordonnées clientes.

*pWndOwner*<br/>
dans Pointeur vers la fenêtre parente du menu contextuel.

*bRightAlign*<br/>
dans Paramètre booléen qui indique comment les éléments de menu sont alignés. Si *bRightAlign* a la valeur true, le menu est aligné à droite pour l’ordre de lecture de droite à gauche. Si *bRightAlign* a la valeur false, le menu est aligné à gauche pour l’ordre de lecture de gauche à droite.

### <a name="return-value"></a>Valeur renvoyée

ID de commande de menu de la commande choisie par l’utilisateur ; 0 si l’utilisateur ferme le menu contextuel sans sélectionner une commande de menu.

### <a name="remarks"></a>Notes

Cette méthode fonctionne comme un appel modal pour afficher un menu contextuel. L’application ne continue pas à la ligne suivante dans le code jusqu’à ce que l’utilisateur ferme le menu contextuel ou sélectionne une commande. Une autre méthode que vous pouvez utiliser pour afficher un menu contextuel est [CContextMenuManager :: ShowPopupMenu](#showpopupmenu). Cette méthode n’est pas un appel modal et ne retourne pas l’ID de la commande sélectionnée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)
