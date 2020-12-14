---
description: 'En savoir plus sur : classe CTabView'
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
ms.openlocfilehash: 59d4169bae108575fcf4844ec7c5c6e1e6681e28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345054"
---
# <a name="ctabview-class"></a>CTabView, classe

La `CTabView` classe simplifie l’utilisation de la classe de contrôle onglet ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) dans les applications qui utilisent l’architecture document/vue de MFC.

## <a name="syntax"></a>Syntaxe

```
class CTabbedView : public CView
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTabView::AddView](#addview)|Ajoute une nouvelle vue au contrôle onglet.|
|[CTabView::FindTab](#findtab)|Retourne l’index de la vue spécifiée dans le contrôle onglet.|
|[CTabView::GetActiveView](#getactiveview)|Retourne un pointeur vers la vue actuellement active|
|[CTabView::GetTabControl](#gettabcontrol)|Retourne une référence au contrôle onglet associé à la vue.|
|[CTabView::RemoveView](#removeview)|Supprime la vue du contrôle onglet.|
|[CTabView::SetActiveView](#setactiveview)|Rend une vue active.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CTabView::IsScrollBar](#isscrollbar)|Appelé par l’infrastructure lors de la création d’une vue d’onglet pour déterminer si la vue d’onglet a une barre de défilement horizontale partagée.|
|[CTabView :: OnActivateView](#onactivateview)|Appelé par le Framework lorsque la vue d’onglet est rendue active ou inactive.|

## <a name="remarks"></a>Notes

Cette classe facilite la mise en forme d’une vue à onglets dans une application document/vue. `CTabView` est une `CView` classe dérivée de qui contient un `CMFCTabCtrl` objet incorporé. `CTabView` gère tous les messages nécessaires à la prise en charge de l' `CMFCTabCtrl` objet. Dérivez simplement une classe de `CTabView` et connectez-la à votre application, puis ajoutez `CView` des classes dérivées à l’aide de la `AddView` méthode. Le contrôle onglet affiche ces vues sous forme d’onglets.

Par exemple, vous pouvez avoir un document qui peut être représenté de différentes façons : sous la forme d’une feuille de calcul, d’un graphique, d’un formulaire modifiable, etc. Vous pouvez créer des vues individuelles qui dessinent les données en fonction des besoins, les insérer dans votre `CTabView` objet dérivé de et les faire passer d’un onglet à l’autre sans codage supplémentaire.

[Exemple TabbedView : l’application de vue à onglets MFC](../../overview/visual-cpp-samples.md) illustre l’utilisation de `CTabView` .

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CTabView` est utilisé dans l’exemple TabbedView.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>Spécifications

**En-tête :** afxTabView. h

## <a name="ctabviewaddview"></a><a name="addview"></a> CTabView::AddView

Ajoute une vue au contrôle onglet.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Paramètres

*pViewClass*<br/>
dans Pointeur vers une classe d’exécution de la vue insérée.

*strViewLabel*<br/>
dans Spécifie le texte de l’onglet.

*iIndex*<br/>
dans Spécifie la position de base zéro au niveau de laquelle insérer la vue. Si la position est-1, le nouvel onglet est inséré à la fin.

*pContext*<br/>
dans Pointeur vers le `CCreateContext` de la vue.

### <a name="return-value"></a>Valeur renvoyée

Index de vue si cette méthode est réussie. Sinon, -1.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter une vue au contrôle onglet incorporé dans un frame.

## <a name="ctabviewfindtab"></a><a name="findtab"></a> CTabView::FindTab

Retourne l’index de la vue spécifiée dans le contrôle onglet.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>Paramètres

*hWndView*<br/>
dans Handle de la vue.

### <a name="return-value"></a>Valeur renvoyée

Index de la vue, s’il est trouvé ; Sinon,-1.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer l’index d’une vue qui a un handle spécifié.

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a> CTabView::GetActiveView

Retourne un pointeur vers la vue actuellement active.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur valide vers la vue active, ou NULL s’il n’y a pas de vue active.

### <a name="remarks"></a>Notes

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a> CTabView::GetTabControl

Retourne une référence au contrôle onglet associé à la vue.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>Valeur renvoyée

Référence au contrôle onglet associé à la vue.

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a> CTabView::IsScrollBar

Appelé par l’infrastructure lors de la création d’une vue d’onglet pour déterminer si la vue d’onglet a une barre de défilement horizontale partagée.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la vue d’onglet doit être créée avec une barre de défilement partagée. Dans le cas contraire, la valeur est FALSE.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsqu’un objet *CTabView* est en cours de création.

Substituez la méthode *IsScrollBar* dans une classe dérivée de *CTabView* et retournez la valeur true si vous souhaitez créer une vue qui a une barre de défilement horizontale partagée.

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a> CTabView :: OnActivateView

Appelé par le Framework lorsque la vue d’onglet est rendue active ou inactive.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>Paramètres

*view*<br/>
dans Pointeur vers la vue.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Substituez cette méthode dans une `CTabView` classe dérivée de pour traiter cette notification.

## <a name="ctabviewremoveview"></a><a name="removeview"></a> CTabView::RemoveView

Supprime la vue du contrôle onglet.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>Paramètres

*iTabNum*<br/>
dans Index de la vue à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Index de la vue supprimée si cette méthode réussit. Sinon-1.

### <a name="remarks"></a>Notes

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a> CTabView::SetActiveView

Rend une vue active.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>Paramètres

*iTabNum*<br/>
dans Index de base zéro de la vue d’onglet.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la vue spécifiée a été rendue active, FALSe si l’index de la vue n’est pas valide.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [CMFCTabCtrl :: SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)
