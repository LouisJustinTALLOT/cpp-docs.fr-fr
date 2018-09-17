---
title: Cmfcmenubutton, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aae4caaa73970818a4c3deee9a82b94260629e17
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700907"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton, classe
Bouton qui affiche un menu contextuel et signale les sélections de l'utilisateur dans les menus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Construit un objet `CMFCMenuButton`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Appelé par l’infrastructure pour traduire les messages de fenêtre avant qu’ils soient distribués. (Substitue `CMFCButton::PreTranslateMessage`.)|  
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Modifie la taille du bouton en fonction de sa taille de texte et image.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Spécifie s’il faut afficher le menu contextuel du système par défaut ou utilisez [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|  
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Spécifie si le menu contextuel s’affiche en dessous ou à droite du bouton.|  
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Spécifie si le bouton de menu modifie son état une fois que l’utilisateur relâche le bouton.|  
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Handle vers le menu Windows attaché.|  
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|L’utilisateur a un identificateur qui indique quel est l’élément sélectionné dans le menu contextuel.|  
  
## <a name="remarks"></a>Notes  
 Le `CMFCMenuButton` classe est dérivée de la [cmfcbutton, classe](../../mfc/reference/cmfcbutton-class.md) , à son tour, dérivée de la [CButton, classe](../../mfc/reference/cbutton-class.md). Par conséquent, vous pouvez utiliser `CMFCMenuButton` dans votre code de la même façon que vous utiliseriez `CButton`.  
  
 Lorsque vous créez un `CMFCMenuButton`, vous devez passer un handle pour le menu contextuel associé. Ensuite, appelez la fonction `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent` vérifie que la taille du bouton est suffisante pour inclure une flèche qui pointe vers l’emplacement où la fenêtre contextuelle s’affiche : à savoir, en dessous ou à droite du bouton.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir le handle du menu attaché au bouton, redimensionner le bouton en fonction de sa taille de texte et image et définir le menu contextuel qui s’affiche par l’infrastructure. Cet extrait de code fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxmenubutton.h  
  
##  <a name="cmfcmenubutton"></a>  CMFCMenuButton::CMFCMenuButton  
 Construit un nouvel [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) objet.  
  
```  
CMFCMenuButton();
```  
  
##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu  
 Une variable de membre de type Boolean qui indique le menu contextuel de l’infrastructure affiche.  
  
```  
BOOL m_bOSMenu;  
```  
  
### <a name="remarks"></a>Notes  
 Si `m_bOSMenu` a la valeur TRUE, le framework appelle héritées `TrackPopupMenu` méthode pour cet objet. Sinon, le framework appelle [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).  
  
##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow  
 Une variable de membre de type Boolean qui indique l’emplacement du menu contextuel.  
  
```  
BOOL m_bRightArrow;  
```  
  
### <a name="remarks"></a>Notes  
 Lorsque l’utilisateur appuie sur le bouton de menu, l’application affiche un menu contextuel. L’infrastructure affiche le menu contextuel sous le bouton ou à droite du bouton. Le bouton possède également une petite flèche qui indique où le menu contextuel s’affiche. Si `m_bRightArrow` a la valeur TRUE, l’infrastructure affiche le menu contextuel à droite du bouton. Sinon, elle affiche le menu contextuel sous le bouton.  
  
##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed  
 Une variable de membre de type Boolean qui indique si le bouton de menu apparaît enfoncé pendant que l’utilisateur effectue une sélection dans le menu contextuel.  
  
```  
BOOL m_bStayPressed;  
```  
  
### <a name="remarks"></a>Notes  
 Si le `m_bStayPressed` membre a la valeur FALSE, le bouton de menu ne pas devenir enfoncé lorsque l’utilisateur clique sur le bouton. Dans ce cas, l’infrastructure affiche uniquement dans le menu contextuel.  
  
 Si le `m_bStayPressed` membre a la valeur TRUE, le bouton de menu devienne enfoncé lorsque l’utilisateur clique sur le bouton. Il reste enfoncé jusqu'à une fois que l’utilisateur ferme le menu contextuel, en effectuant une sélection ou l’annulation.  
  
##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu  
 Le handle du menu attaché.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="remarks"></a>Notes  
 L’infrastructure affiche le menu indiqué par cette variable membre lorsqu’il clique sur le bouton de menu.  
  
##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult  
 Entier qui indique quel élément de l’utilisateur sélectionne dans le menu contextuel.  
  
```  
int m_nMenuResult;  
```  
  
### <a name="remarks"></a>Notes  
 La valeur de cette variable de membre est égal à zéro si l’utilisateur annule le menu sans avoir à effectuer une sélection ou si une erreur se produit.  
  
##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage  
 Appelé par l’infrastructure pour traduire les messages de fenêtre avant qu’ils soient distribués.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
*pMsg*<br/>
[in] Pointe vers un [MSG](../../mfc/reference/msg-structure1.md) structure qui contient le message à traiter.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le message a été traduit et ne doit pas être distribué ; 0 si le message n’était pas traduit et doit être distribué.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent  
 Modifie la taille du bouton en fonction de sa taille du texte et la taille de l’image.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
*bCalcOnly*<br/>
[in] Un paramètre booléen qui indique si cette méthode redimensionne le bouton.  
  
### <a name="return-value"></a>Valeur de retour  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet qui spécifie la nouvelle taille pour le bouton.  
  
### <a name="remarks"></a>Notes  
 Si vous appelez cette fonction et *bCalcOnly* a la valeur TRUE, `SizeToContent` calcule uniquement la nouvelle taille du bouton.  
  
 La nouvelle taille du bouton est calculée en fonction de flèche, l’image et le texte du bouton. Le framework ajoute également des marges prédéfinies de 10 pixels du bord horizontal et de 5 pixels du bord vertical.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCButton, classe](../../mfc/reference/cmfcbutton-class.md)
