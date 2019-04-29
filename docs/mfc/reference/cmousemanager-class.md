---
title: Cmousemanager, classe
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
ms.openlocfilehash: f92a72e36fecbb39e57cbdf9583047aca0c1ebd5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338244"
---
# <a name="cmousemanager-class"></a>Cmousemanager, classe

Permet à un utilisateur d’associer différentes commandes à un particulier [CView](../../mfc/reference/cview-class.md) lorsque l’utilisateur double-clique à l’intérieur de cette vue de l’objet.

## <a name="syntax"></a>Syntaxe

```
class CMouseManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Ajoute un `CView` de l’objet à la **personnalisation** boîte de dialogue. Le **personnalisation** boîte de dialogue permet à l’utilisateur à associer une commande pour chacune des vues répertoriées dans un double-clic.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Retourne la commande est exécutée lorsque l’utilisateur double-clique à l’intérieur de la vue fournie.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Retourne l’icône associée à l’ID de la vue fournis.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Retourne l’ID de la vue associée au nom d’affichage fourni.|
|[CMouseManager::GetViewNames](#getviewnames)|Récupère une liste de tous les noms de vue ajouté.|
|[CMouseManager::LoadState](#loadstate)|Charge le `CMouseManager` état à partir du Registre Windows.|
|[CMouseManager::SaveState](#savestate)|Écrit le `CMouseManager` état dans le Registre Windows.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Associe la commande fournie et la vue fournie.|

## <a name="remarks"></a>Notes

Le `CMouseManager` classe maintient une collection de `CView` objets. Chaque vue est identifié par un nom et par un code. Ces vues sont affichées dans le **personnalisation** boîte de dialogue. L’utilisateur peut modifier la commande qui est associée à n’importe quelle vue via la **personnalisation** boîte de dialogue. La commande associée est exécutée quand l’utilisateur double-clique dans cette vue. Pour prendre en charge ce point de vue de codage, vous devez traiter le message WM_LBUTTONDBLCLK et appelez le [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) fonction dans le code correspondant `CView` objet...

Vous ne devez pas créer un `CMouseManager` objet manuellement. Il est créé par l’infrastructure de votre application. Il sera également détruit automatiquement lorsque l’utilisateur quitte l’application. Pour obtenir un pointeur vers le Gestionnaire de la souris pour votre application, appelez [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxmousemanager.h

##  <a name="addview"></a>  CMouseManager::AddView

Inscrit un [CView](../../mfc/reference/cview-class.md) de l’objet avec le [cmousemanager, classe](../../mfc/reference/cmousemanager-class.md) pour prendre en charge le comportement de la souris personnalisé.

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
[in] Un ID de la vue.

*uiViewNameResId*<br/>
[in] Un ID de chaîne de ressource qui référence le nom de la vue.

*uiIconId*<br/>
[in] Un ID d’icône de vue.

*iId*<br/>
[in] Un ID de la vue.

*lpszViewName*<br/>
[in] Un nom de la vue.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Pour prendre en charge du comportement de la souris personnalisé, une vue doit être enregistrée avec le `CMouseManager` objet. N’importe quel objet dérivé de la `CView` classe permettre être inscrits auprès du Gestionnaire de la souris. La chaîne et l’icône associée à une vue sont affichés dans le **souris** onglet de la **personnaliser** boîte de dialogue.

Il incombe au programmeur de créer et maintenir telles que les ID de vue *iViewId* et *iId*.

Pour plus d’informations sur la façon de fournir un comportement personnalisé de la souris, consultez [personnalisation du clavier et souris](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer un pointeur vers un `CMouseManager` objet à l’aide de la `CWinAppEx::GetMouseManager` (méthode) et le `AddView` méthode dans la `CMouseManager` classe. Cet extrait de code fait partie de la [échantillon de collecte de l’état](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

##  <a name="getviewdblclickcommand"></a>  CMouseManager::GetViewDblClickCommand

Retourne la commande est exécutée lorsque l’utilisateur double-clique à l’intérieur de la vue fournie.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Paramètres

*iId*<br/>
[in] L’ID de la vue.

### <a name="return-value"></a>Valeur de retour

L’identificateur de commande si la vue est associée à une commande ; sinon 0.

##  <a name="getviewiconid"></a>  CMouseManager::GetViewIconId

Récupère l’icône associée à un ID de la vue.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Paramètres

*iViewId*<br/>
[in] L’ID de la vue.

### <a name="return-value"></a>Valeur de retour

Un identificateur de ressource d’icône en cas de réussite ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode échoue si la vue n’est pas inscrit tout d’abord à l’aide de [CMouseManager::AddView](#addview).

##  <a name="getviewidbyname"></a>  CMouseManager::GetViewIdByName

Récupère l’ID de vue associé à un nom de la vue.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
[in] Le nom de la vue.

### <a name="return-value"></a>Valeur de retour

Un ID de vue en cas de réussite ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode effectue une recherche dans les vues enregistrées à l’aide de [CMouseManager::AddView](#addview).

##  <a name="getviewnames"></a>  CMouseManager::GetViewNames

Récupère une liste de tous les noms d’affichage inscrits.

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Paramètres

*listOfNames*<br/>
[out] Une référence à `CStringList` objet.

### <a name="remarks"></a>Notes

Cette méthode remplit le paramètre `listOfNames` avec les noms de toutes les vues inscrits à l’aide de [CMouseManager::AddView](#addview).

##  <a name="loadstate"></a>  CMouseManager::LoadState

Charge l’état de la [cmousemanager, classe](../../mfc/reference/cmousemanager-class.md) à partir du Registre.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Un chemin d’accès d’une clé de Registre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les informations d’état chargées à partir du Registre incluent les vues inscrits, les identificateurs de vue et les commandes associées. Si le paramètre *lpszProfileName* est NULL, cette fonction charge le `CMouseManager` données à partir de l’emplacement de Registre par défaut contrôlé par le [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md).

Dans la plupart des cas, il est inutile d’appeler cette fonction directement. Il est appelé dans le cadre du processus d’initialisation espace de travail. Pour plus d’informations sur le processus d’initialisation de l’espace de travail, consultez [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

##  <a name="savestate"></a>  CMouseManager::SaveState

Écrit l’état de la [cmousemanager, classe](../../mfc/reference/cmousemanager-class.md) dans le Registre.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[in] Un chemin d’accès d’une clé de Registre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les informations d’état écrites dans le Registre incluent inscrits toutes les vues, les identificateurs de vue et les commandes associées. Si le paramètre *lpszProfileName* est NULL, cette fonction écrit le `CMouseManager` données à l’emplacement de Registre par défaut contrôlé par le [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md).

Dans la plupart des cas, il est inutile d’appeler cette fonction directement. Il est appelé dans le cadre du processus de sérialisation d’espace de travail. Pour plus d’informations sur le processus de sérialisation d’espace de travail, consultez [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

##  <a name="setcommandfordblclk"></a>  CMouseManager::SetCommandForDblClk

Associe une commande personnalisée à une vue qui est inscrit dans le Gestionnaire de la souris.

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*iViewId*<br/>
[in] L’identificateur de la vue.

*uiCmd*<br/>
[in] Identificateur de commande.

### <a name="remarks"></a>Notes

Pour associer une commande personnalisée à une vue, vous devez tout d’abord enregistrer la vue à l’aide de [CMouseManager::AddView](#addview). Le `AddView` méthode requiert un identificateur d’affichage comme paramètre d’entrée. Une fois que vous enregistrez une vue, vous pouvez appeler `CMouseManager::SetCommandForDblClk` avec le même identificateur d’entrée paramètre view que vous avez fournies à `AddView`. Par la suite, lorsque l’utilisateur double-clique sur la souris dans la vue inscrite, l’application exécute la commande indiquée par *uiCmd.* Pour prendre en charge le comportement de la souris personnalisé, vous devez également personnaliser l’affichage inscrit auprès du Gestionnaire de la souris. Pour plus d’informations sur le comportement de la souris personnalisé, consultez [personnalisation du clavier et souris](../keyboard-and-mouse-customization.md).

Si *uiCmd* est définie sur 0, la vue spécifiée n’est plus associée à une commande.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[Personnalisation du clavier et de la souris](../../mfc/keyboard-and-mouse-customization.md)
