---
title: CDragListBox, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
dev_langs:
- C++
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a32963ebb6bfbfcb1063e8eda678693bec872e79
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337282"
---
# <a name="cdraglistbox-class"></a>CDragListBox, classe
En plus de fournir les fonctionnalités d’une zone de liste Windows, le `CDragListBox` classe permet à l’utilisateur déplacer des éléments de liste, tels que des noms de fichiers, au sein de la zone de liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDragListBox : public CListBox  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](#cdraglistbox)|Construit un objet `CDragListBox`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](#begindrag)|Appelé par le framework lorsqu’une opération glisser commence.|  
|[CDragListBox::CancelDrag](#canceldrag)|Appelé par le framework lorsqu’une opération glisser a été annulée.|  
|[CDragListBox::Dragging](#dragging)|Appelé par l’infrastructure pendant une opération glisser.|  
|[CDragListBox::DrawInsert](#drawinsert)|Dessine le guide d’insertion de la zone de liste de glissement.|  
|[CDragListBox::Dropped](#dropped)|Appelé par l’infrastructure après que l’élément a été supprimé.|  
|[CDragListBox::ItemFromPt](#itemfrompt)|Retourne les coordonnées de l’élément déplacé.|  
  
## <a name="remarks"></a>Notes  
 Avec cette fonctionnalité, les zones de liste permettent aux utilisateurs classer les éléments dans une liste de quelque manière plus utile. Par défaut, la zone de liste sera déplacer l’élément vers le nouvel emplacement dans la liste. Toutefois, `CDragListBox` objets peuvent être personnalisés pour copier des éléments au lieu de les déplacer.  
  
 Le contrôle de zone de liste est associé le `CDragListBox` classe ne doit pas avoir le LBS_SORT ou le style LBS_MULTIPLESELECT. Pour obtenir une description de styles de zone de liste, consultez [Styles de zone de liste](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).  
  
 Pour utiliser une zone de liste glisser dans une boîte de dialogue existante de votre application, ajoutez un contrôle de zone de liste à votre modèle de boîte de dialogue à l’aide de l’éditeur de boîtes de dialogue et ensuite affecter une variable membre (de catégorie `Control` et le Type de Variable `CDragListBox`) correspondant à la zone de liste contrôler dans votre modèle de boîte de dialogue.  
  
 Pour plus d’informations sur l’attribution des contrôles à des variables de membre, consultez [raccourci pour la définition des Variables membres pour les contrôles de boîte de dialogue](../../windows/defining-member-variables-for-dialog-controls.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcmn.h  
  
##  <a name="begindrag"></a>  CDragListBox::BeginDrag  
 Appelé par le framework lorsque survient un événement qui pourrait commencer une opération glisser, par exemple en appuyant sur le bouton gauche de la souris.  
  
```  
virtual BOOL BeginDrag(CPoint pt);
```  
  
### <a name="parameters"></a>Paramètres  
 *pt*  
 Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet qui contient les coordonnées de l’élément déplacé.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le glissement est autorisé, sinon 0.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction si vous souhaitez contrôler que se passe-t-il quand une opération glisser commence. L’implémentation par défaut capture la souris et reste en mode glisser jusqu'à ce que l’utilisateur clique sur le bouton gauche ou droit de la souris ou appuie sur ÉCHAP, moment auquel l’opération glisser est annulée.  
  
##  <a name="canceldrag"></a>  CDragListBox::CancelDrag  
 Appelé par le framework lorsqu’une opération glisser a été annulée.  
  
```  
virtual void CancelDrag(CPoint pt);
```  
  
### <a name="parameters"></a>Paramètres  
 *pt*  
 Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet qui contient les coordonnées de l’élément déplacé.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour gérer tout traitement spécial pour votre contrôle de zone de liste.  
  
##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox  
 Construit un objet `CDragListBox`.  
  
```  
CDragListBox();
```  
  
##  <a name="dragging"></a>  CDragListBox::Dragging  
 Appelé par l’infrastructure quand un élément de zone de liste est déplacé dans le `CDragListBox` objet.  
  
```  
virtual UINT Dragging(CPoint pt);
```  
  
### <a name="parameters"></a>Paramètres  
 *pt*  
 Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet qui contient les coordonnées x et y coordonnées du curseur d’écran.  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID de ressource du curseur à afficher. Les valeurs suivantes sont possibles :  
  
- DL_COPYCURSOR indique que l’élément sera copié.  
  
- DL_MOVECURSOR indique que l’élément doit être déplacé.  
  
- DL_STOPCURSOR indique que la cible de dépôt actuelle n’est pas acceptable.  
  
### <a name="remarks"></a>Notes  
 Le comportement par défaut retourne DL_MOVECURSOR. Remplacez cette fonction si vous souhaitez fournir des fonctionnalités supplémentaires.  
  
##  <a name="drawinsert"></a>  CDragListBox::DrawInsert  
 Appelé par l’infrastructure pour dessiner le guide d’insertion avant l’élément possédant l’index indiqué.  
  
```  
virtual void DrawInsert(int nItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de base zéro du point d’insertion.  
  
### <a name="remarks"></a>Notes  
 Une valeur de - 1 efface le guide d’insertion. Remplacez cette fonction pour modifier l’apparence ou le comportement du guide d’insertion.  
  
##  <a name="dropped"></a>  CDragListBox::Dropped  
 Appelé par le framework lorsqu’un élément est supprimé au sein d’un `CDragListBox` objet.  
  
```  
virtual void Dropped(
    int nSrcIndex,  
    CPoint pt);
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcIndex*  
 Spécifie l’index de base zéro de la chaîne supprimée.  
  
 *pt*  
 Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet qui contient les coordonnées du site de dépôt.  
  
### <a name="remarks"></a>Notes  
 Le comportement par défaut copie l’élément de zone de liste et ses données vers le nouvel emplacement, puis supprime l’élément d’origine. Remplacez cette fonction pour personnaliser le comportement par défaut, telles que l’activation des copies des éléments de zone de liste à faire glisser vers d’autres emplacements au sein de la liste.  
  
##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt  
 Appel de cette fonction pour récupérer l’index de base zéro de l’élément de zone de liste située à *pt*.  
  
```  
int ItemFromPt(
    CPoint pt,  
    BOOL bAutoScroll = TRUE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pt*  
 Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objet contenant les coordonnées d’un point dans la zone de liste.  
  
 *bAutoScroll*  
 Différent de zéro si le défilement est autorisé, sinon 0.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de l’élément de zone de liste de glissement.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC TSTCON](../../visual-cpp-samples.md)   
 [CListBox (classe)](../../mfc/reference/clistbox-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CListBox, classe](../../mfc/reference/clistbox-class.md)
