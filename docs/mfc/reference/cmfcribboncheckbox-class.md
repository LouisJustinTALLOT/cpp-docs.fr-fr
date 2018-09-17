---
title: Cmfcribboncheckbox, classe | Microsoft Docs
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
ms.openlocfilehash: 44ccd0c1625e971fd74e913b9618d7f3ae811be5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712489"
---
# <a name="cmfcribboncheckbox-class"></a>Cmfcribboncheckbox, classe
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
où *nID* est l’ID de commande de case à cocher et *lpszText* représente l’étiquette de texte de la case à cocher.  
  
 Vous pouvez ajouter une case à cocher à un panneau de ruban à l’aide de [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxribboncheckbox.h  
  
##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 Constructeur d’un objet de case à cocher du ruban  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
*nID*<br/>
[in] Spécifie l’ID de commande.  
  
*lpszText*<br/>
[in] Spécifie l’étiquette de texte.  
  
### <a name="return-value"></a>Valeur de retour  
 Construit un objet de case à cocher du ruban.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCRibbonCheckBox` classe.  
  
 [!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize  
 En cas de substitution, obtient la taille réduite de la case à cocher.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
*contrôleur de domaine principal*<br/>
[in] Pointeur vers la capture de données modifiées associé à la case à cocher.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CSize` objet qui contient la taille réduite de la case à cocher.  
  
### <a name="remarks"></a>Notes  
 Si ne pas de substitution, retourne la taille intermédiaire de la case à cocher.  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize  
 Obtient la taille intermédiaire de la case à cocher.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
*contrôleur de domaine principal*<br/>
[in] Pointeur vers la capture de données modifiées associée à cette case à cocher.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CSize` objet contenant la taille intermédiaire de la case à cocher.  
  
### <a name="remarks"></a>Notes  
 Si ne pas substituée, calcule la taille intermédiaire en tant que la taille de la case à cocher par défaut ( `AFX_CHECK_BOX_DEFAULT_SIZE`) ainsi que la taille du texte, ainsi que les marges.  
  
##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize  
 Obtient la taille normale de la case à cocher.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
*contrôleur de domaine principal*<br/>
[in] Pointeur vers l’objet de capture de données modifiées associé à cette case à cocher.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CSize` objet qui contient la taille normale de la case à cocher.  
  
### <a name="remarks"></a>Notes  
 Si ne pas de substitution, retourne la taille intermédiaire de la case à cocher.  
  
##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage  
 Indique s’il existe une image de l’info-bulle associée à la case à cocher.  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE s’il existe une image de l’info-bulle associée à la case à cocher, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw  
 Appelé par l’infrastructure pour dessiner la case à cocher à l’aide d’un contexte de périphérique spécifié.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
*contrôleur de domaine principal*<br/>
[in] Pointeur vers la capture de données modifiées dans lequel dessiner la case à cocher.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage  
 Appelé par l’infrastructure pour dessiner une image de menu pour la case à cocher.  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *Capture de données modifiées**  
 Pointeur vers la capture de données modifiées associé à la case à cocher.  
  
*CRect*<br/>
[in] Un `CRect` objet qui spécifie le rectangle dans lequel dessiner l’image de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE si l’image a été dessinée, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Si ne pas de substitution, retourne FALSE.  
  
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
*contrôleur de domaine principal*<br/>
[in] Pointeur vers le contexte de périphérique dans lequel dessiner la case à cocher.  
  
*strText*<br/>
[in] Texte affiché.  
  
*nTextOffset*<br/>
[in] La distance, en pixels, du côté gauche de la zone de liste pour afficher un texte.  
  
*Rect*<br/>
[in] Le rectangle d’affichage pour la case à cocher.  
  
*bIsSelected*<br/>
[in] TRUE si la case à cocher est sélectionnée, ou FALSE dans le cas contraire.  
  
*bHighlighted*<br/>
[in] TRUE si la case à cocher est mis en surbrillance, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData  
 Définit les données d’accessibilité pour la case à cocher.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParent*  
 La fenêtre parente de la case à cocher.  
  
 *data*  
 Les données d’accessibilité pour la case à cocher.  
  
### <a name="return-value"></a>Valeur de retour  
 Renvoie toujours TRUE.  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette méthode définit les données d’accessibilité pour la case à cocher et retourne toujours la valeur TRUE. Remplacez cette méthode pour définir l’accessibilité des données et retourner une valeur qui indique la réussite ou l’échec.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel, classe](../../mfc/reference/cmfcribbonpanel-class.md)
