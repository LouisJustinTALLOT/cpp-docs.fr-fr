---
title: Classe de CMFCRibbonSlider | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06575c4d014f72ddbae63ea5f02c3081b4228e1d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037723"
---
# <a name="cmfcribbonslider-class"></a>Classe de CMFCRibbonSlider
La `CMFCRibbonSlider` classe implémente un contrôle de curseur que vous pouvez ajouter à une barre de ruban ou la barre d’état du ruban. Le contrôle Slider de ruban ressemble aux curseurs de zoom présents dans les applications Office 2007.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Construit et initialise un contrôle slider de ruban.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonSlider::GetPos](#getpos)|Retourne la position actuelle du contrôle slider.|  
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Retourne la valeur maximale du curseur.|  
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Retourne la valeur minimale du curseur.|  
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Retourne la taille normale de l'élément de ruban. (Substitue [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Retourne la taille de l’incrément de zoom pour le contrôle slider.|  
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Spécifie si le curseur a des boutons de zoom.|  
|[CMFCRibbonSlider::OnDraw](#ondraw)|Appelé par l'infrastructure pour dessiner l'élément de ruban. (Substitue [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonSlider::SetPos](#setpos)|Définit la position actuelle du contrôle slider.|  
|[CMFCRibbonSlider::SetRange](#setrange)|Spécifie la plage du contrôle slider en définissant les valeurs minimales et maximales.|  
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Affiche ou masque les boutons de zoom.|  
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Définit la taille de l’incrément de zoom pour le contrôle slider.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la `SetRange` méthode permettant de configurer la plage d’incréments de zoom pour le curseur. Vous pouvez définir la position actuelle du curseur à l’aide de la `SetPos` (méthode).  
  
 Vous pouvez afficher les boutons de zoom circulaire sur les côtés gauche et droit du contrôle slider à l’aide de la `SetZoomButtons` (méthode). Par défaut, le curseur est horizontal, le bouton Zoom sur la gauche affiche un signe moins et le bouton droit de zoom affiche un signe plus.  
  
 Le `SetZoomIncrement` méthode définit l’incrément à ajouter ou soustraire de la position actuelle lorsqu’un utilisateur clique sur les boutons de zoom.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCRibbonSlider` classe pour définir les propriétés du curseur. L’exemple montre comment construire un `CMFCRibbonSlider` de l’objet, afficher les boutons de zoom, définir la position actuelle du contrôle slider et définir la plage de valeurs pour le contrôle slider.  
  
 [!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxribbonslider.h  
  
##  <a name="cmfcribbonslider"></a>  CMFCRibbonSlider::CMFCRibbonSlider  
 Construire un slider de ruban.  
  
```  
CMFCRibbonSlider(
    UINT nID,  
    int nWidth=100);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nID*  
 ID de curseur.  
  
 [in]. *nWidth*  
 Largeur du curseur en pixels.  
  
### <a name="remarks"></a>Notes  
 Construit un slider de ruban est *nWidth* pixels en larges dans la catégorie du Panneau de configuration où le curseur est ajouté. Par défaut, le curseur est horizontal.  
  
##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos  
 Retourne la position actuelle du contrôle slider.  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La position actuelle du contrôle de curseur, ce qui correspond à une position par rapport au début du curseur.  
  
##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax  
 Obtient l’incrément maximal du curseur qui peut être acheminées par le curseur sur le contrôle slider.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’incrément maximal du curseur qui peut être acheminées par le curseur sur le contrôle slider.  
  
##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin  
 Retourne l’incrément minimale qui peut être acheminées par le curseur sur le contrôle slider.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’incrément minimale qui peut être acheminées par le curseur sur le contrôle slider.  
  
##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement  
 Obtenir l’incrément de zoom pour le contrôle slider.  
  
```  
int GetZoomIncrement() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’incrément de zoom pour le contrôle slider.  
  
##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons  
 Spécifie si le curseur a des boutons de zoom.  
  
```  
BOOL HasZoomButtons() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le curseur comporte des boutons de zoom ; `FALSE` dans le cas contraire.  
  
##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos  
 Définir la position actuelle du contrôle slider.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nPos*  
 Spécifie la position à définir pour le curseur. La position est relatif au début du curseur.  
  
 [in] *bRedraw*  
 Si `TRUE`, le curseur est redessiné.  
  
##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange  
 Définir la plage de valeurs pour le contrôle slider.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nMin*  
 Spécifie la valeur minimale du contrôle slider.  
  
 [in] *nombre maximal*  
 Spécifie la valeur maximale du contrôle slider.  
  
### <a name="remarks"></a>Notes  
 Spécifie la plage de valeurs pour le contrôle de curseur en définissant les valeurs minimales et maximales.  
  
##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons  
 Afficher ou masquer les boutons de zoom.  
  
```  
void SetZoomButtons(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in]. *bSet*  
 `TRUE` Pour afficher les boutons de zoom ; `FALSE` pour les masquer.  
  
##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement  
 Définissez l’incrément de zoom pour le contrôle slider.  
  
```  
void SetZoomIncrement(int nZoomIncrement);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nZoomIncrement*  
 Spécifie l’incrément de zoom du contrôle slider.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement, classe](../../mfc/reference/cmfcribbonbaseelement-class.md)
