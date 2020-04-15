---
title: CTabView, classe
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: ad30cbbf5de195708d2d357a76c38b661d095c2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365919"
---
# <a name="ctabview-class"></a>CTabView, classe

La `CTabView` classe simplifie l’utilisation de la classe de contrôle de l’onglet ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) dans les applications qui utilisent l’architecture de document/vue de MFC.

## <a name="syntax"></a>Syntaxe

```
class CTabbedView : public CView
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTabView::AddView](#addview)|Ajoute une nouvelle vue au contrôle de l’onglet.|
|[CTabView::FindTab](#findtab)|Retourne l’index de la vue spécifiée dans le contrôle de l’onglet.|
|[CTabView::GetActiveView](#getactiveview)|Retourne un pointeur à la vue actuellement active|
|[CTabView::GetTabControl](#gettabcontrol)|Renvoie une référence au contrôle de l’onglet associé à la vue.|
|[CTabView::RemoveView](#removeview)|Retire la vue du contrôle de l’onglet.|
|[CTabView::SetActiveView](#setactiveview)|Rend une vue active.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CTabView::IsScrollBar](#isscrollbar)|Appelé par le cadre lors de la création d’une vue d’onglet pour déterminer si la vue de l’onglet a une barre de défilement horizontal partagé.|
|[CTabView::OnActivateView](#onactivateview)|Appelé par le cadre lorsque la vue de l’onglet est rendue active ou inactive.|

## <a name="remarks"></a>Notes

Cette classe facilite la mise d’une vue onglet dans une application document/vue. `CTabView`est `CView`une classe dérivée `CMFCTabCtrl` qui contient un objet intégré. `CTabView`gère tous les messages `CMFCTabCtrl` requis pour prendre en charge l’objet. Il suffit de `CTabView` tirer une classe et `CView`le brancher dans `AddView` votre application, puis ajouter des classes dérivées en utilisant la méthode. Le contrôle de l’onglet affichera ces vues sous forme d’onglets.

Par exemple, vous pouvez avoir un document qui peut être représenté de différentes manières : comme feuille de calcul, graphique, formulaire modifiable, etc. Vous pouvez créer des vues individuelles dessinant `CTabView`les données au besoin, les insérer dans votre objet dérivé et les faire ongletr sans aucun codage supplémentaire.

[Échantillon De TabbedView : L’application de vue tabbed de MFC](../../overview/visual-cpp-samples.md) illustre l’utilisation de `CTabView`.

## <a name="example"></a>Exemple

L’exemple suivant `CTabView` montre comment est utilisé dans l’échantillon TabbedView.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>Spécifications

**En-tête:** afxTabView.h

## <a name="ctabviewaddview"></a><a name="addview"></a>CTabView::AddView

Ajoute une vue au contrôle de l’onglet.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Paramètres

*pViewClass (en)*<br/>
[dans] Un pointeur à une classe de runtime de la vue insérée.

*strViewLabel (en)*<br/>
[dans] Spécifie le texte de l’onglet.

*iIndex (en)*<br/>
[dans] Spécifie la position zéro à laquelle insérer la vue. Si la position est de -1, le nouvel onglet est inséré à la fin.

*pContext*<br/>
[dans] Un pointeur `CCreateContext` à la vue.

### <a name="return-value"></a>Valeur de retour

Un indice de vue si cette méthode réussit. Sinon, -1.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter une vue au contrôle de l’onglet qui est intégré dans un cadre.

## <a name="ctabviewfindtab"></a><a name="findtab"></a>CTabView::FindTab

Retourne l’index de la vue spécifiée dans le contrôle de l’onglet.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>Paramètres

*hWndView (en)*<br/>
[dans] Le manche de la vue.

### <a name="return-value"></a>Valeur de retour

L’index de la vue s’il est trouvé; sinon, -1.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer l’index d’une vue qui a une poignée spécifiée.

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView::GetActiveView

Retourne un pointeur à la vue actuellement active.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide à la vue active, ou NULL s’il n’y a pas de vue active.

### <a name="remarks"></a>Notes

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView::GetTabControl

Renvoie une référence au contrôle de l’onglet associé à la vue.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>Valeur de retour

Une référence au contrôle de l’onglet associé à la vue.

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a>CTabView::IsScrollBar

Appelé par le cadre lors de la création d’une vue d’onglet pour déterminer si la vue de l’onglet a une barre de défilement horizontal partagé.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la vue de l’onglet doit être créée avec une barre de défilement partagée. Dans le cas contraire, la valeur est FALSE.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsqu’un objet *CTabView* est créé.

Remplacez la méthode *IsScrollBar* dans une classe dérivée de *CTabView*et retournez TRUE si vous souhaitez créer une vue qui dispose d’une barre de défilement horizontale partagée.

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a>CTabView::OnActivateView

Appelé par le cadre lorsque la vue de l’onglet est rendue active ou inactive.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>Paramètres

*Vue*<br/>
[dans] Un pointeur à la vue.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Remplacer cette méthode `CTabView`dans une classe dérivée pour traiter cette notification.

## <a name="ctabviewremoveview"></a><a name="removeview"></a>CTabView::RemoveView

Retire la vue du contrôle de l’onglet.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>Paramètres

*iTabNum (en)*<br/>
[dans] L’index de la vue à supprimer.

### <a name="return-value"></a>Valeur de retour

L’index de la vue supprimée si cette méthode réussit. Sinon -1.

### <a name="remarks"></a>Notes

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView::SetActiveView

Rend une vue active.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>Paramètres

*iTabNum (en)*<br/>
[dans] L’indice zéro de la vue de l’onglet.

### <a name="return-value"></a>Valeur de retour

VRAI si la vue spécifiée a été rendue active, FALSE si l’indice de la vue est invalide.

### <a name="remarks"></a>Notes

Pour plus d’informations voir [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)
