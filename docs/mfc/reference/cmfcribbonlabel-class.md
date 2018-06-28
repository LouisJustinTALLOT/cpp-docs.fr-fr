---
title: Classe de CMFCRibbonLabel | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36b2d78bb3f1ffaefa67a062c6498c195d46336f
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042493"
---
# <a name="cmfcribbonlabel-class"></a>Classe de CMFCRibbonLabel
Implémente une étiquette de texte non interactive pour un ruban.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Construit et initialise un `CMFCRibbonLabel` objet avec la chaîne de texte spécifié.|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCRibbonLabel::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|`CMFCRibbonLabel::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Détermine les données d’accessibilité de l’élément label de ruban en cours. (Substitue [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
### <a name="remarks"></a>Notes  
 Après avoir créé une étiquette de ruban, ajoutez-le à un panneau en appelant [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
 Impossible d’ajouter une étiquette de ruban à la barre d’outils Accès rapide.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxRibbonLabel.h  
  
##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel  
 Construit et initialise un [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) objet qui affiche la chaîne de texte spécifiée.  
  
```  
CMFCRibbonLabel(
    LPCTSTR lpszText,  
    BOOL bIsMultiLine = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszText*  
 Le texte à afficher dans l’étiquette.  
  
 [in] *bIsMultiLine*  
 `TRUE` Pour spécifier que l’étiquette est une étiquette multiligne. dans le cas contraire, `FALSE`.  
  
##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData  
 Détermine les données d’accessibilité de l’élément label de ruban en cours.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pParent*  
 Représente la fenêtre parente de l’étiquette de ruban actuelle.  
  
 [out] *données*  
 Un objet de type `CAccessibilityData` qui est remplie avec les données d’accessibilité de l’étiquette de ruban actuelle.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le *données* paramètre a été correctement remplis avec les données d’accessibilité de l’étiquette de ruban actuelle ; sinon, `FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
