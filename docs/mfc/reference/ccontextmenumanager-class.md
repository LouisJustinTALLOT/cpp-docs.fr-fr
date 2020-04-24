---
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
ms.openlocfilehash: c676355ebf44d6cc02bfa66ac870757627ae5a58
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754806"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager, classe

L’objet `CContextMenuManager` gère des menus de raccourci, également connus sous le nom de menus contextuels.

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
|[CContextMenuManager::AddMenu](#addmenu)|Ajoute un nouveau menu raccourci.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Retourne une poignée au menu associé à l’ID de ressources fournie.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Retourne une poignée au menu qui correspond au nom du menu fourni.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Retourne une liste de noms de menu.|
|[CContextMenuManager::LoadState](#loadstate)|Charge les menus de raccourcis stockés dans le registre Windows.|
|[CContextMenuManager::ResetState](#resetstate)|Efface les menus raccourcis du gestionnaire de menu contextuel.|
|[CContextMenuManager::SaveState](#savestate)|Enregistre les menus de raccourcis au registre Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Contrôle si `CContextMenuManager` le ferme le menu raccourci actif quand il montre un nouveau menu raccourci.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Affiche le menu raccourci spécifié.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Affiche le menu raccourci spécifié. Retourne l’index de la commande de menu sélectionnée.|

## <a name="remarks"></a>Notes

`CContextMenuManager`gère les menus de raccourci et s’assure qu’ils ont une apparence cohérente.

Vous ne devez `CContextMenuManager` pas créer un objet manuellement. Le cadre de votre `CContextMenuManager` application crée l’objet. Toutefois, vous devez appeler [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) lorsque votre application est parascée. Après l’initialisation du gestionnaire de contexte, utilisez la méthode [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) pour obtenir un pointeur au gestionnaire de contexte pour votre application.

Vous pouvez créer des menus raccourcis à l’heure d’exécution en appelant `AddMenu`. Si vous souhaitez afficher le menu sans `ShowPopupMenu`recevoir d’abord l’entrée de l’utilisateur, appelez . `TrackPopupMenu`est utilisé lorsque vous souhaitez créer un menu et attendre l’entrée de l’utilisateur. `TrackPopupMenu`retourne l’index de la commande sélectionnée ou 0 si l’utilisateur est sorti sans rien sélectionner.

Le `CContextMenuManager` peut également enregistrer et charger son état au registre Windows.

## <a name="example"></a>Exemple

L’exemple suivant montre comment ajouter `CContextMenuManager` un menu à un objet, et comment `CContextMenuManager` ne pas fermer le menu pop-up actif lorsque l’objet affiche un nouveau menu pop-up. Cet extrait de code fait partie de [l’échantillon de pages personnalisées](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Spécifications

**En-tête:** afxcontextmenumanager.h

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a>CContextMenuManager::AddMenu

Ajoute un nouveau menu raccourci au [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

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
[dans] Une pièce d’identité de ressource pour une chaîne qui contient le nom du nouveau menu.

*uiMenuResId*<br/>
[dans] L’ID de la ressource du menu.

*lpszName (en)*<br/>
[dans] Une chaîne qui contient le nom du nouveau menu.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode a été couronnée de succès; 0 si la méthode échoue.

### <a name="remarks"></a>Notes

Cette méthode échoue si *uiMenuResId* est invalide ou si `CContextMenuManager`un autre menu avec le même nom est déjà dans le .

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

Construit un objet [CContextMenuManager.](../../mfc/reference/ccontextmenumanager-class.md)

```
CContextMenuManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous ne devez pas créer un `CContextMenuManager` manuellement. Le cadre de votre `CContextMenuManager` application crée l’objet. Vous devez appeler [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) lors de l’initialisation de votre application. Pour obtenir un pointeur pour le gestionnaire de contexte, appelez [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a>CContextMenuManager::GetMenuById

Retourne une poignée au menu associé à une pièce d’identité de ressource donnée.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Paramètres

*nMenuResId (en anglais)*<br/>
[dans] L’ID de ressource pour le menu.

### <a name="return-value"></a>Valeur de retour

Une poignée au menu `NULL` associé ou si le menu n’est pas trouvé.

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

Retourne une poignée à un menu spécifique.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
[dans] Une chaîne qui contient le nom du menu à récupérer.

*puiOrigResID*<br/>
[out] Un pointeur à un UINT. Ce paramètre contient l’ID de ressource du menu spécifié, s’il est trouvé.

### <a name="return-value"></a>Valeur de retour

Une poignée au menu qui correspond au nom qui a été spécifié par *lpszName*. NULL s’il n’y a pas de menu appelé *lpszName*.

### <a name="remarks"></a>Notes

Si cette méthode trouve un menu qui `GetMenuByName` correspond *lpszName*, stocke l’ID de ressource de menu dans le *paramètre puiOrigResID*.

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a>CContextMenuManager::GetMenuNames

Retourne la liste des noms de menu ajoutés au [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```cpp
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Paramètres

*listeOfNames*<br/>
[out] Une référence à un paramètre [CStringList.](../../mfc/reference/cstringlist-class.md) Cette méthode écrit la liste des noms de menu à ce paramètre.

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a>CContextMenuManager::LoadState

Charge les informations associées à la [classe CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) du registre Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Une chaîne qui contient le chemin relatif d’une clé de registre.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode est réussie; sinon 0.

### <a name="remarks"></a>Notes

Le paramètre *lpszProfileName* n’est pas le chemin absolu pour une entrée de registre. Il s’agit d’un chemin relatif qui est ajouté à la fin de la clé de registre par défaut pour votre demande. Pour obtenir ou définir la clé de registre par défaut, utilisez les méthodes [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) et [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) respectivement.

Utilisez la méthode [CContextMenuManager::SaveState](#savestate) pour enregistrer les menus raccourcis au registre.

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a>CContextMenuManager::ResetState

Efface tous les éléments des menus de raccourcis associés à la [classe CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode est réussie; FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode efface les menus pop-up et `CContextMenuManager`les supprime de la .

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a>CContextMenuManager::SaveState

Enregistre les informations associées à la [classe CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) au registre Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Une chaîne qui contient le chemin relatif d’une clé de registre.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode est réussie; sinon 0.

### <a name="remarks"></a>Notes

Le paramètre *lpszProfileName* n’est pas le chemin absolu pour une entrée de registre. Il s’agit d’un chemin relatif qui est ajouté à la fin de la clé de registre par défaut pour votre demande. Pour obtenir ou définir la clé de registre par défaut, utilisez les méthodes [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) et [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) respectivement.

Utilisez la méthode [CContextMenuManager::LoadState](#loadstate) pour charger les menus raccourcis du registre.

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

Contrôle si le [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) ferme le menu pop-up actif lorsqu’il affiche un nouveau menu pop-up.

```cpp
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSet (en anglais)*<br/>
[dans] Un paramètre Boolean qui contrôle s’il faut fermer le menu pop-up actif. Une valeur de TRUE indique que le menu pop-up actif n’est pas fermé. FALSE indique que le menu pop-up actif est fermé.

### <a name="remarks"></a>Notes

Par défaut, `CContextMenuManager` le ferme le menu pop-up actif.

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu

Affiche le menu raccourci spécifié.

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
[dans] L’ID de ressource du menu que cette méthode affichera.

*x*<br/>
[dans] Le décalage horizontal pour le menu raccourci dans les coordonnées des clients.

*y*<br/>
[dans] Le décalage vertical pour le menu raccourci dans les coordonnées des clients

*pWndOwner (en)*<br/>
[dans] Un pointeur à la fenêtre parente du menu raccourci.

*bOwnMessage (en)*<br/>
[dans] Un paramètre Boolean qui indique comment les messages sont acheminés. Si *bOwnMessage* est FALSE, le routage MFC standard est utilisé. Sinon, *pWndOwner* reçoit les messages.

*hmenuPopup*<br/>
[dans] Le manche du menu que cette méthode affichera.

*bAutoDestroy*<br/>
[dans] Un paramètre Boolean qui indique si le menu sera automatiquement détruit.

*bRightAlign (en)*<br/>
[dans] Un paramètre Boolean qui indique comment les éléments du menu sont alignés. Si *bRightAlign* est VRAI, le menu est aligné à droite pour l’ordre de lecture de droite à gauche.

### <a name="return-value"></a>Valeur de retour

La première surcharge de méthode renvoie nonzero si la méthode montre le menu avec succès; sinon 0. La deuxième surcharge de méthode renvoie un pointeur à [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) si le menu raccourci s’affiche correctement; autrement NULL.

### <a name="remarks"></a>Notes

Cette méthode ressemble à la méthode [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) en ce que les deux méthodes affichent un menu raccourci. Toutefois, `TrackPopupMenu` retourne l’index de la commande de menu sélectionnée.

Si le paramètre *bAutoDestroy* est FALSE, `DestroyMenu` vous devez appeler manuellement la méthode héritée pour libérer les ressources de mémoire. La mise `ShowPopupMenu` en œuvre par défaut de n’utilise pas le paramètre *bAutoDestroy*. Il est prévu pour une utilisation future `CContextMenuManager` ou pour des classes personnalisées dérivées de la classe .

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu

Affiche le menu raccourci spécifié et renvoie l’index de la commande de menu raccourci sélectionnée.

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
[dans] Le manche du menu raccourci que cette méthode affiche.

*x*<br/>
[dans] Le décalage horizontal pour le menu raccourci dans les coordonnées des clients.

*y*<br/>
[dans] Le décalage vertical pour le menu raccourci dans les coordonnées des clients.

*pWndOwner (en)*<br/>
[dans] Un pointeur à la fenêtre parente du menu raccourci.

*bRightAlign (en)*<br/>
[dans] Un paramètre Boolean qui indique comment les éléments du menu sont alignés. Si *bRightAlign* est VRAI, le menu est aligné à droite pour l’ordre de lecture de droite à gauche. Si *bRightAlign* est FALSE, le menu est aligné de gauche pour l’ordre de lecture de gauche à droite.

### <a name="return-value"></a>Valeur de retour

L’ID de commande de menu de la commande que l’utilisateur choisit ; 0 si l’utilisateur ferme le menu raccourci sans sélectionner une commande de menu.

### <a name="remarks"></a>Notes

Cette méthode fonctionne comme un appel modal pour afficher un menu raccourci. L’application ne continuera pas à la ligne suivante dans le code jusqu’à ce que l’utilisateur ferme le menu raccourci ou sélectionne une commande. Une méthode alternative que vous pouvez utiliser pour afficher un menu raccourci est [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Cette méthode n’est pas un appel modal et ne retournera pas l’ID de la commande sélectionnée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)
