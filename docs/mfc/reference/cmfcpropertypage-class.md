---
title: Classe de CMFCPropertyPage | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3352841b1b495d1718ffa6be034239ecd7e50c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366640"
---
# <a name="cmfcpropertypage-class"></a>Classe de CMFCPropertyPage
La `CMFCPropertyPage` classe prend en charge l’affichage des menus contextuels sur une page de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Construit un objet `CMFCPropertyPage`.|  
|`CMFCPropertyPage::~CMFCPropertyPage`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|`CMFCPropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|`CMFCPropertyPage::OnSetActive`|Cette fonction membre est appelée par le framework lorsque la page est choisie par l’utilisateur et devient la page active. (Substitue [notifications CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|  
|`CMFCPropertyPage::PreTranslateMessage`|Convertit les messages de fenêtre avant d’être distribués à le [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) fonctions Windows. Pour plus d’informations et la syntaxe de méthode, consultez [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CPropertyPage::PreTranslateMessage`.)|  
  
## <a name="remarks"></a>Notes  
 La `CMFCPropertyPage` classe représente des pages individuelles d’une feuille de propriétés, également appelée boîte de dialogue à onglets.  
  
 Utilisez le `CMFCPropertyPage` classe avec le [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) classe. Pour utiliser les menus sur une page de propriétés, remplacez toutes les occurrences de la `CPropertyPage` classe avec la `CMFCPropertyPage` classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxpropertypage.h  
  
##  <a name="cmfcpropertypage"></a>  CMFCPropertyPage::CMFCPropertyPage  
 Construit un objet `CMFCPropertyPage`.  
  
```  
CMFCPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption=0);

 
CMFCPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption=0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDTemplate`  
 ID de ressource du modèle pour cette page.  
  
 `nIDCaption`  
 ID de ressource de l’étiquette à placer dans l’onglet de cette page. Si 0, le nom est obtenu à partir de la boîte de dialogue modèle de cette page. La valeur par défaut est 0.  
  
 `lpszTemplateName`  
 Pointe vers le nom du modèle pour cette page. Ne peut pas être `NULL`.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les paramètres du constructeur, consultez [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertySheet, classe](../../mfc/reference/cmfcpropertysheet-class.md)
