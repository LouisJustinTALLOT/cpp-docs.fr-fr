---
title: Classe de CTabView | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d64d503c4bad0d452be174064e2932ed100d7de
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121755"
---
# <a name="ctabview-class"></a>Classe de CTabView
Le `CTabView` classe simplifie l’utilisation de la classe du contrôle onglet ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) dans les applications qui utilisent l’architecture document/vue de MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|Ajoute un nouvel affichage au contrôle onglet.|  
|[CTabView::FindTab](#findtab)|Retourne l’index de la vue spécifiée dans le contrôle onglet.|  
|[CTabView::GetActiveView](#getactiveview)|Retourne un pointeur vers la vue actuellement active.|  
|[CTabView::GetTabControl](#gettabcontrol)|Retourne une référence au contrôle onglet associé à la vue.|  
|[CTabView::RemoveView](#removeview)|Supprime l’affichage du contrôle onglet.|  
|[CTabView::SetActiveView](#setactiveview)|Rend une vue active.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|Appelé par l’infrastructure lors de la création d’une vue de l’onglet pour déterminer si la vue de l’onglet a une barre de défilement horizontale partagé.|  
|[CTabView::OnActivateView](#onactivateview)|Appelé par le framework lorsque la vue de l’onglet devient actif ou inactif.|  
  
## <a name="remarks"></a>Notes  
 Cette classe rend facile de placer une vue à onglets dans une application de document/vue. `CTabView` est un `CView`-classe dérivée qui contient un élément incorporé `CMFCTabCtrl` objet. `CTabView` gère tous les messages requis pour prendre en charge la `CMFCTabCtrl` objet. Simplement dériver une classe de `CTabView` et connectez-le à votre application, puis ajoutez `CView`-classes dérivées à l’aide de la `AddView` (méthode). Le contrôle onglet affiche ces vues sous forme d’onglets.  
  
 Par exemple, vous pouvez avoir un document qui peut être représenté de différentes manières : en tant qu’une feuille de calcul, un graphique, d’un formulaire modifiable et ainsi de suite. Vous pouvez créer des vues tracer les données en fonction des besoins, les insérer dans votre `CTabView`-objet dérivé et les onglets sans aucun codage supplémentaire.  
  
 [TabbedView, exemple : Application de la vue à onglets MFC](../../visual-cpp-samples.md) illustre l’utilisation de `CTabView`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment `CTabView` est utilisé dans l’exemple TabbedView.  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxTabView.h  
  
##  <a name="addview"></a>  CTabView::AddView  
 Ajouter un affichage au contrôle onglet.  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pViewClass*  
 Pointeur vers une classe d’exécution de la vue insérée.  
  
 [in] *strViewLabel*  
 Spécifie le texte de l’onglet.  
  
 [in] *iIndex*  
 Spécifie la position de base zéro au niveau duquel insérer la vue. Si la position est -1, le nouvel onglet est inséré à la fin.  
  
 [in] *pContext*  
 Un pointeur vers le `CCreateContext` de la vue.  
  
### <a name="return-value"></a>Valeur de retour  
 Un index de la vue si cette méthode réussit. Sinon, -1.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour ajouter une vue pour le contrôle d’onglet est incorporé dans un frame.  
  
##  <a name="findtab"></a>  CTabView::FindTab  
 Retourne l’index de la vue spécifiée dans le contrôle onglet.  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *hWndView*  
 Le handle de la vue.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de la vue s’il est trouvé ; Sinon, -1.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour récupérer l’index d’une vue possédant un handle spécifié.  
  
##  <a name="getactiveview"></a>  CTabView::GetActiveView  
 Retourne un pointeur vers la vue actuellement active.  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Obtenir un pointeur valide vers la vue active, ou NULL s’il n’existe aucune vue active.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gettabcontrol"></a>  CTabView::GetTabControl  
 Retourne une référence au contrôle onglet associé à la vue.  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence au contrôle onglet associé à la vue.  
  
##  <a name="isscrollbar"></a>  CTabView::IsScrollBar  
 Appelé par l’infrastructure lors de la création d’une vue de l’onglet pour déterminer si la vue de l’onglet a une barre de défilement horizontale partagé.  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la vue de l’onglet doit être créée avec une barre de défilement partagé. Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode lorsqu’un *CTabView* objet est créé.  
  
 Remplacer la *IsScrollBar* méthode dans un *CTabView*-classe dérivée et renvoie la valeur TRUE si vous souhaitez créer une vue qui a une barre de défilement horizontale partagé.  
  
##  <a name="onactivateview"></a>  CTabView::OnActivateView  
 Appelé par le framework lorsque la vue de l’onglet devient actif ou inactif.  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *affichage*  
 Pointeur vers la vue.  
  
### <a name="remarks"></a>Notes  
 L'implémentation par défaut n'exécute aucune opération. Substituez cette méthode dans un `CTabView`-classe pour traiter cette notification dérivée.  
  
##  <a name="removeview"></a>  CTabView::RemoveView  
 Supprime l’affichage du contrôle onglet.  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iTabNum*  
 Index de la vue à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de la vue supprimée si cette méthode réussit. Sinon,-1.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setactiveview"></a>  CTabView::SetActiveView  
 Rend une vue active.  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iTabNum*  
 Index de base zéro de la vue de l’onglet.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la vue spécifiée devient active, FALSE si l’index de vue n’est pas valide.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [CView, classe](../../mfc/reference/cview-class.md)
