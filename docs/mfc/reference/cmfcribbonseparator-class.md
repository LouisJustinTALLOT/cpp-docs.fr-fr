---
title: Classe de CMFCRibbonSeparator | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1c4c3b286f020d8d409b344c5d8c05ebc200425
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370856"
---
# <a name="cmfcribbonseparator-class"></a>Classe de CMFCRibbonSeparator
Implémente le séparateur de ruban.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonSeparator : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Construit un objet `CMFCRibbonSeparator`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Ajoute un séparateur à la **commandes** liste dans le **personnaliser** boîte de dialogue. (Substitue [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|  
|`CMFCRibbonSeparator::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|`CMFCRibbonSeparator::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Une méthode de copie qui définit les membres d’un séparateur variables à partir d’un autre objet.|  
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Retourne la taille d’un séparateur.|  
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Indique s’il s’agit d’un séparateur.|  
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Indique s’il s’agit d’un taquet de tabulation.|  
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Appelée par le système pour dessiner le séparateur sur le ruban ou la barre d’outils Accès rapide.|  
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Appelée par le système pour dessiner le séparateur sur le **commandes** liste.|  
  
## <a name="remarks"></a>Notes  
 Un séparateur de ruban est une ligne verticale ou horizontale que logiquement sépare éléments de ruban. Un séparateur peut être dessiné sur le contrôle du ruban, le menu de l’application principale, la barre d’état du ruban et la barre d’outils Accès rapide.  
  
 Pour utiliser un séparateur dans votre application, construisez le nouvel objet et l’ajouter dans le menu application principale, comme indiqué ici :  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```  
Appelez [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) pour ajouter des séparateurs pour les volets de ruban. Les séparateurs sont alloués et ajoutés en interne par le `AddSeparator` (méthode).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxbaseribbonelement.h  
  
##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox  
 Ajoute un séparateur à la **commandes** liste dans le **personnaliser** boîte de dialogue.  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndListBox`  
 Un pointeur vers le **commandes** où est ajouté le séparateur de liste.  
  
 [in] `bDeep`  
 Ignoré.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de la chaîne dans la zone de liste spécifiée par `pWndListBox`.  
  
##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator  
 Construit un objet `CMFCRibbonSeparator`.  
  
```  
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bIsHoriz`  
 Si `TRUE`, le séparateur est horizontal ; si `FALSE`, le séparateur est vertical.  
  
### <a name="remarks"></a>Notes  
 Séparateurs horizontaux sont utilisées dans les menus de l’application. Séparateurs verticaux sont utilisés dans les barres d’outils.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCRibbonSeparator` classe.  
  
 [!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom  
 Une méthode de copie qui définit les membres d’un séparateur variables à partir d’un autre objet.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `Src`  
 L’élément de ruban source d’origine.  
  
##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize  
 Retourne la taille d’un séparateur.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contenu de l’appareil.  
  
### <a name="return-value"></a>Valeur de retour  
 La taille du séparateur dans le contexte de périphérique donné.  
  
##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator  
 Indique s’il s’agit d’un séparateur.  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Toujours `TRUE` à cette classe.  
  
##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop  
 Indique s’il s’agit d’un taquet de tabulation.  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Toujours `FALSE` à cette classe.  
  
### <a name="remarks"></a>Notes  
 Un séparateur de ruban n’est pas un taquet de tabulation.  
  
##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw  
 Appelée par le système pour dessiner le séparateur sur le ruban ou la barre d’outils Accès rapide.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList  
 Appelée par le système pour dessiner le séparateur sur le **commandes** liste.  
  
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
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `pDC`|Pointeur vers un contexte de périphérique.|  
|[in] `strText`|Texte affiché dans la liste.|  
|[in] `nTextOffset`|Espacement entre le texte et le côté gauche du rectangle englobant.|  
|[in] `rect`|Spécifie le rectangle englobant.|  
|[in] `bIsSelected`|Ignoré.|  
|[in] `bHighlighted`|Ignoré.|  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
