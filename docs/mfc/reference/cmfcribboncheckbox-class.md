---
title: Classe de CMFCRibbonCheckBox | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 109c3b2f6337adece6c371f1fafa98291468485e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribboncheckbox-class"></a>Classe de CMFCRibbonCheckBox
La classe `CMFCRibbonCheckBox` implémente une case à cocher que vous pouvez ajouter à un volet du ruban, une barre d'outils Accès rapide ou un menu contextuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Substitue [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Substitue [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Substitue [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Substitue `CMFCRibbonButton::IsDrawTooltipImage`.)|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Substitue [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Substitue [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Substitue `CMFCRibbonButton::OnDrawOnList`.)|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Substitue [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
## <a name="remarks"></a>Notes  
 Pour utiliser un `CMFCRibbonCheckBox` dans votre application, ajoutez le constructeur suivant à votre code :  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
où `nID` correspond à l'ID de commande de case à cocher et `lpszText` représente l'étiquette de texte de la case à cocher.  
  
 Vous pouvez ajouter une case à cocher à un panneau de ruban à l’aide de [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxribboncheckbox.h  
  
##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 Constructeur d’un objet de la case à cocher du ruban  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nID`  
 Spécifie l’ID de commande.  
  
 [in] `lpszText`  
 Spécifie l’étiquette de texte.  
  
### <a name="return-value"></a>Valeur de retour  
 Construit un objet de la case à cocher du ruban.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCRibbonCheckBox` classe.  
  
 [!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize  
 En cas de substitution, obtient la taille réduite de la case à cocher.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers le `CDC` associé à la case à cocher.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CSize` objet qui contient la taille réduite de la case à cocher.  
  
### <a name="remarks"></a>Notes  
 Si ne pas substituée, retourne la taille intermédiaire de la case à cocher.  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize  
 Obtient la taille intermédiaire de la case à cocher.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers le `CDC` associé à cette case à cocher.  
  
### <a name="return-value"></a>Valeur de retour  
 A `CSize` objet contenant la taille intermédiaire de la case à cocher.  
  
### <a name="remarks"></a>Notes  
 Si ne pas substituée, calcule la taille intermédiaire en tant que la taille de la case à cocher par défaut ( `AFX_CHECK_BOX_DEFAULT_SIZE`) ainsi que la taille du texte, ainsi que les marges.  
  
##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize  
 Obtient la taille normale de la case à cocher.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers le `CDC` objet associé à cette case à cocher.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CSize` objet qui contient la taille normale de la case à cocher.  
  
### <a name="remarks"></a>Notes  
 Si ne pas substituée, retourne la taille intermédiaire de la case à cocher.  
  
##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage  
 Indique s’il existe une image de l’info-bulle associée à la case à cocher.  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` s’il existe une image de l’info-bulle associée à la case à cocher, ou `FALSE` si ce n’est pas le cas.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw  
 Appelé par l’infrastructure pour dessiner la case à cocher à l’aide d’un contexte de périphérique spécifié.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers le `CDC` dans lequel dessiner la case à cocher.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage  
 Appelé par l’infrastructure pour dessiner une image de menu pour la case à cocher.  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `CDC*`  
 Pointeur vers le `CDC` associé à la case à cocher.  
  
 [in] `CRect`  
 A `CRect` objet qui spécifie le rectangle dans lequel dessiner l’image de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` si l’image a été dessinée, ou `FALSE` si ce n’est pas le cas.  
  
### <a name="remarks"></a>Notes  
 Si ne pas substituée, retourne `FALSE`.  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonCheckBox::OnDrawOnList  
 Appelé par l’infrastructure pour dessiner la case à cocher dans une zone de liste de commandes.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers le contexte de périphérique dans lequel dessiner la case à cocher.  
  
 [in] `strText`  
 Le texte d’affichage.  
  
 [in] `nTextOffset`  
 La distance, en pixels, du côté gauche de la zone de liste pour afficher du texte.  
  
 [in] `rect`  
 Le rectangle d’affichage de la case à cocher.  
  
 [in] `bIsSelected`  
 `TRUE` Si la case à cocher est activée, ou `FALSE` si ce n’est pas le cas.  
  
 [in] `bHighlighted`  
 `TRUE` Si la case à cocher est sélectionnée, ou `FALSE` si ce n’est pas le cas.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData  
 Définit les données d’accessibilité de la case à cocher.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParent`  
 La fenêtre parente de la case à cocher.  
  
 `data`  
 Données d’accessibilité de la case à cocher.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Par défaut cette méthode définit les données d’accessibilité de la case à cocher et always retourne `TRUE`. Remplacez cette méthode pour définir l’accessibilité des données et retourner une valeur qui indique la réussite ou l’échec.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel, classe](../../mfc/reference/cmfcribbonpanel-class.md)
