---
description: 'En savoir plus sur : classe CMouseManager'
title: CMouseManager, classe
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: 9816583aa9d05b76f97f1be1487898b5827fbcae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331552"
---
# <a name="cmousemanager-class"></a>CMouseManager, classe

Permet à un utilisateur d’associer différentes commandes à un objet [CView](../../mfc/reference/cview-class.md) particulier lorsque l’utilisateur double-clique à l’intérieur de cette vue.

## <a name="syntax"></a>Syntaxe

```
class CMouseManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Ajoute un `CView` objet à la boîte de dialogue de **personnalisation** . La boîte de dialogue **personnalisation** permet à l’utilisateur d’associer un double-clic à une commande pour chacune des vues listées.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Retourne la commande qui est exécutée lorsque l’utilisateur double-clique à l’intérieur de la vue fournie.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Retourne l’icône associée à l’ID de vue fourni.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Retourne l’ID de vue associé au nom de vue fourni.|
|[CMouseManager::GetViewNames](#getviewnames)|Récupère une liste de tous les noms de vues ajoutés.|
|[CMouseManager :: LoadState](#loadstate)|Charge l' `CMouseManager` État à partir du Registre Windows.|
|[CMouseManager :: saveste](#savestate)|Écrit l' `CMouseManager` État dans le Registre Windows.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Associe la commande fournie et la vue fournie.|

## <a name="remarks"></a>Notes

La `CMouseManager` classe gère une collection d' `CView` objets. Chaque vue est identifiée par un nom et un ID. Ces affichages sont affichés dans la boîte de dialogue **personnalisation** . L’utilisateur peut modifier la commande associée à n’importe quelle vue via la boîte de dialogue **personnalisation** . La commande associée est exécutée lorsque l’utilisateur double-clique sur cette vue. Pour le prendre en charge, du point de vue du codage, vous devez traiter le message WM_LBUTTONDBLCLK et appeler la fonction [CWinAppEx :: OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) dans le code de cet `CView` objet.

Vous ne devez pas créer un `CMouseManager` objet manuellement. Il sera créé par l’infrastructure de votre application. Il est également détruit automatiquement lorsque l’utilisateur quitte l’application. Pour obtenir un pointeur vers le gestionnaire de la souris de votre application, appelez [CWinAppEx :: GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmousemanager. h

## <a name="cmousemanageraddview"></a><a name="addview"></a> CMouseManager::AddView

Inscrit un objet [CView](../../mfc/reference/cview-class.md) avec la [classe CMouseManager](../../mfc/reference/cmousemanager-class.md) pour prendre en charge le comportement de souris personnalisé.

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>Paramètres

*iViewId*<br/>
dans ID de vue.

*uiViewNameResId*<br/>
dans ID de chaîne de ressource qui référence le nom de la vue.

*uiIconId*<br/>
dans ID d’icône d’affichage.

*Vaut*<br/>
dans ID de vue.

*lpszViewName*<br/>
dans Nom de la vue.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Afin de prendre en charge le comportement de la souris personnalisée, une vue doit être inscrite avec l' `CMouseManager` objet. Tout objet dérivé de la `CView` classe peut être inscrit avec le gestionnaire de souris. La chaîne et l’icône associées à une vue s’affichent dans l’onglet **souris** de la boîte de dialogue **personnaliser** .

Il incombe au programmeur de créer et de gérer des ID d’affichage tels que *iViewId* et *IID*.

Pour plus d’informations sur la façon de fournir un comportement de souris personnalisé, consultez [Personnalisation du clavier et de la souris](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer un pointeur vers un `CMouseManager` objet à l’aide de la `CWinAppEx::GetMouseManager` méthode et `AddView` de la méthode dans la `CMouseManager` classe. Cet extrait de code fait partie de l' [exemple de collection d’État](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a> CMouseManager::GetViewDblClickCommand

Retourne la commande qui est exécutée lorsque l’utilisateur double-clique à l’intérieur de la vue fournie.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Paramètres

*Vaut*<br/>
dans ID de la vue.

### <a name="return-value"></a>Valeur renvoyée

Identificateur de commande si la vue est associée à une commande ; Sinon, 0.

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a> CMouseManager::GetViewIconId

Récupère l’icône associée à un ID de vue.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Paramètres

*iViewId*<br/>
dans ID de la vue.

### <a name="return-value"></a>Valeur renvoyée

Identificateur de ressource d’icône en cas de réussite ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode échoue si la vue n’est pas inscrite pour la première fois à l’aide de [CMouseManager :: AddView](#addview).

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a> CMouseManager::GetViewIdByName

Récupère l’ID de vue associé à un nom de vue.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
dans Nom de la vue.

### <a name="return-value"></a>Valeur renvoyée

ID de vue en cas de réussite ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode effectue une recherche dans les vues inscrites à l’aide de [CMouseManager :: AddView](#addview).

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a> CMouseManager::GetViewNames

Récupère une liste de tous les noms de vues inscrits.

```cpp
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Paramètres

*listOfNames*<br/>
à Référence à l' `CStringList` objet.

### <a name="remarks"></a>Notes

Cette méthode remplit le paramètre `listOfNames` avec les noms de toutes les vues inscrites à l’aide de [CMouseManager :: AddView](#addview).

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a> CMouseManager :: LoadState

Charge l’état de la [classe CMouseManager](../../mfc/reference/cmousemanager-class.md) à partir du Registre.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Chemin d’accès à une clé de registre.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les informations d’État chargées à partir du Registre incluent les vues inscrites, les identificateurs de vue et les commandes associées. Si le paramètre *lpszProfileName* est null, cette fonction charge les `CMouseManager` données à partir de l’emplacement de Registre par défaut contrôlé par la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md).

Dans la plupart des cas, il n’est pas nécessaire d’appeler cette fonction directement. Elle est appelée dans le cadre du processus d’initialisation de l’espace de travail. Pour plus d’informations sur le processus d’initialisation de l’espace de travail, consultez [CWinAppEx :: LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

## <a name="cmousemanagersavestate"></a><a name="savestate"></a> CMouseManager :: saveste

Écrit l’état de la [classe CMouseManager](../../mfc/reference/cmousemanager-class.md) dans le registre.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Chemin d’accès à une clé de registre.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les informations d’État écrites dans le registre incluent tous les affichages inscrits, les identificateurs de vue et les commandes associées. Si le paramètre *lpszProfileName* est null, cette fonction écrit les `CMouseManager` données dans l’emplacement de Registre par défaut contrôlé par la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md).

Dans la plupart des cas, il n’est pas nécessaire d’appeler cette fonction directement. Elle est appelée dans le cadre du processus de sérialisation de l’espace de travail. Pour plus d’informations sur le processus de sérialisation de l’espace de travail, consultez [CWinAppEx :: saveste](../../mfc/reference/cwinappex-class.md#savestate).

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a> CMouseManager::SetCommandForDblClk

Associe une commande personnalisée à une vue qui est d’abord enregistrée avec le gestionnaire de souris.

```cpp
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*iViewId*<br/>
dans Identificateur d’affichage.

*uiCmd*<br/>
[in] Identificateur de commande.

### <a name="remarks"></a>Notes

Pour associer une commande personnalisée à une vue, vous devez d’abord inscrire la vue à l’aide de [CMouseManager :: AddView](#addview). La `AddView` méthode requiert un identificateur de vue comme paramètre d’entrée. Une fois que vous avez inscrit une vue, vous pouvez appeler `CMouseManager::SetCommandForDblClk` avec le même paramètre d’entrée d’identificateur de vue que celui que vous avez fourni à `AddView` . Ensuite, lorsque l’utilisateur double-clique sur la souris dans la vue inscrite, l’application exécute la commande indiquée par *uiCmd.* Pour prendre en charge le comportement de souris personnalisé, vous devrez également personnaliser la vue inscrite avec le gestionnaire de souris. Pour plus d’informations sur le comportement personnalisé de la souris, consultez [Personnalisation du clavier et de la souris](../keyboard-and-mouse-customization.md).

Si *uiCmd* a la valeur 0, la vue spécifiée n’est plus associée à une commande.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[Personnalisation du clavier et de la souris](../../mfc/keyboard-and-mouse-customization.md)
