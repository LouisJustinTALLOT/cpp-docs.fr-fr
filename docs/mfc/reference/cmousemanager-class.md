---
title: Classe CMouseManager
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
ms.openlocfilehash: 1394a1b47a86022e37b11e032b87ee2a2a369862
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752808"
---
# <a name="cmousemanager-class"></a>Classe CMouseManager

Permet à un utilisateur d’associer différentes commandes à un objet [CView](../../mfc/reference/cview-class.md) particulier lorsque l’utilisateur double-clics à l’intérieur de cette vue.

## <a name="syntax"></a>Syntaxe

```
class CMouseManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Ajoute `CView` un objet à la boîte de dialogue **De Personnalisation.** La boîte de dialogue **Customization** permet à l’utilisateur d’associer un double clic à une commande pour chacune des vues énumérées.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Retourne la commande qui est exécutée lorsque l’utilisateur double-clics à l’intérieur de la vue fournie.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Renvoie l’icône associée à l’ID de vue fourni.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Renvoie l’ID de vue associé au nom de vue fourni.|
|[CMouseManager::GetViewNames](#getviewnames)|Récupère une liste de tous les noms de vue ajoutés.|
|[CMouseManager::LoadState](#loadstate)|Charge l’état `CMouseManager` à partir du registre Windows.|
|[CMouseManager::SaveState](#savestate)|Écrit `CMouseManager` l’état au registre Windows.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Associe la commande fournie et la vue fournie.|

## <a name="remarks"></a>Notes

La `CMouseManager` classe conserve une `CView` collection d’objets. Chaque vue est identifiée par un nom et par une pièce d’identité. Ces vues sont affichées dans la boîte de dialogue **de personnalisation.** L’utilisateur peut modifier la commande associée à n’importe quelle vue à travers la boîte de dialogue **Customization.** La commande associée est exécutée lorsque l’utilisateur double-clics dans cette vue. Pour prendre en charge cela d’un point de vue de codage, vous devez traiter le message WM_LBUTTONDBLCLK et `CView` appeler le [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) fonction dans le code pour cet objet.

Vous ne devez `CMouseManager` pas créer un objet manuellement. Il sera créé par le cadre de votre application. Il sera également détruit automatiquement lorsque l’utilisateur quittera l’application. Pour obtenir un pointeur au gestionnaire de souris pour votre application, appelez [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmousemanager.h

## <a name="cmousemanageraddview"></a><a name="addview"></a>CMouseManager::AddView

Enregistre un objet [CView](../../mfc/reference/cview-class.md) avec la [classe CMouseManager](../../mfc/reference/cmousemanager-class.md) pour soutenir le comportement personnalisé de la souris.

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

*iViewId (en)*<br/>
[dans] Une carte d’identité.

*uiViewNameResId*<br/>
[dans] Une pièce d’identité de chaîne de ressources qui fait référence au nom de vue.

*uiIconId*<br/>
[dans] Une carte d’icône.

*Iid*<br/>
[dans] Une carte d’identité.

*lpszViewName (en)*<br/>
[dans] Un nom de vue.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Afin de prendre en charge le comportement personnalisé `CMouseManager` de la souris, une vue doit être enregistrée avec l’objet. Tout objet dérivé `CView` de la classe peut être enregistré auprès du gestionnaire de souris. La chaîne et l’icône associées à une vue sont affichées dans **l’onglet Mouse** de la boîte de dialogue **Customize.**

Il est de la responsabilité du programmeur de créer et de maintenir des ID vues telles que *iViewId* et *iId*.

Pour plus d’informations sur la façon de fournir un comportement personnalisé de la souris, voir [Clavier et Mouse Customization](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer `CMouseManager` un pointeur `CWinAppEx::GetMouseManager` sur `AddView` un objet `CMouseManager` en utilisant la méthode et la méthode de la classe. Cet extrait de code fait partie de [l’échantillon de la collection d’État](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand

Retourne la commande qui est exécutée lorsque l’utilisateur double-clics à l’intérieur de la vue fournie.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] L’ID de vue.

### <a name="return-value"></a>Valeur de retour

L’identifiant de commande si la vue est associée à une commande; sinon 0.

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a>CMouseManager::GetViewIconId

Récupère l’icône associée à une pièce d’identité de vue.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Paramètres

*iViewId (en)*<br/>
[dans] L’ID de vue.

### <a name="return-value"></a>Valeur de retour

Un identifiant de ressource d’icône en cas de succès ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode échouera si la vue n’est pas d’abord enregistrée en utilisant [CMouseManager::AddView](#addview).

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a>CMouseManager::GetViewIdByName

Récupère l’ID de vue associé à un nom de vue.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
[dans] Le nom de vue.

### <a name="return-value"></a>Valeur de retour

Une pièce d’identité de vue en cas de succès; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode recherche à travers les vues enregistrées à l’aide [de CMouseManager::AddView](#addview).

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a>CMouseManager::GetViewNames

Récupère une liste de tous les noms de vue enregistrés.

```cpp
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Paramètres

*listeOfNames*<br/>
[out] Une référence `CStringList` à l’objet.

### <a name="remarks"></a>Notes

Cette méthode remplit `listOfNames` le paramètre avec les noms de toutes les vues enregistrées à l’aide [de CMouseManager::AddView](#addview).

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a>CMouseManager::LoadState

Charge l’état de la [classe CMouseManager](../../mfc/reference/cmousemanager-class.md) du registre.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Un chemin d’une clé de registre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les informations d’état chargées du registre comprennent les vues enregistrées, les identifiants de vue et les commandes associées. Si le paramètre *lpszProfileName* est NULL, cette fonction charge les données de l’emplacement `CMouseManager` du registre par défaut contrôlé par la classe [CWinAppEx](../../mfc/reference/cwinappex-class.md).

Dans la plupart des cas, vous n’avez pas à appeler cette fonction directement. Il est appelé dans le cadre du processus d’initialisation de l’espace de travail. Pour plus d’informations sur le processus d’initialisation de l’espace de travail, voir [CWinAppEx:LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

## <a name="cmousemanagersavestate"></a><a name="savestate"></a>CMouseManager::SaveState

Écrit l’état de la [classe CMouseManager](../../mfc/reference/cmousemanager-class.md) au registre.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Un chemin d’une clé de registre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les informations d’état écrites au registre comprennent toutes les vues enregistrées, les identifiants de vue et les commandes associées. Si le paramètre *lpszProfileName* est `CMouseManager` NULL, cette fonction écrit les données à l’emplacement du registre par défaut contrôlé par la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md).

Dans la plupart des cas, vous n’avez pas à appeler cette fonction directement. Il est appelé dans le cadre du processus de sérialisation de l’espace de travail. Pour plus d’informations sur le processus de sérialisation de l’espace de travail, voir [CWinAppEx:SaveState](../../mfc/reference/cwinappex-class.md#savestate).

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk

Associe une commande personnalisée avec une vue qui est d’abord enregistrée auprès du gestionnaire de souris.

```cpp
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*iViewId (en)*<br/>
[dans] L’identifiant de vue.

*uiCmd uiCmd*<br/>
[in] Identificateur de commande.

### <a name="remarks"></a>Notes

Afin d’associer une commande personnalisée à une vue, vous devez d’abord enregistrer la vue en utilisant [CMouseManager::AddView](#addview). La `AddView` méthode nécessite un identifiant de vue comme paramètre d’entrée. Une fois que vous enregistrez une vue, vous pouvez `CMouseManager::SetCommandForDblClk` `AddView`appeler avec le même paramètre d’entrée d’identification de vue que vous avez fourni à . Par la suite, lorsque l’utilisateur double-clics de la souris dans la vue enregistrée, l’application exécutera la commande indiquée par *uiCmd.* Pour prendre en charge le comportement personnalisé de la souris, vous devrez également personnaliser la vue enregistrée auprès du gestionnaire de souris. Pour plus d’informations sur le comportement personnalisé de la souris, voir [Keyboard et Mouse Customization](../keyboard-and-mouse-customization.md).

Si *uiCmd* est réglé à 0, la vue spécifiée n’est plus associée à une commande.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[Personnalisation du clavier et de la souris](../../mfc/keyboard-and-mouse-customization.md)
