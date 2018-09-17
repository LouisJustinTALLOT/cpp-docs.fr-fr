---
title: Cmfcribboncustomizedialog, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d342ec75fd45224dcd36ba3fc17aa1a6f8c12e33
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720653"
---
# <a name="cmfcribboncustomizedialog-class"></a>Cmfcribboncustomizedialog, classe
Affiche le ruban **personnaliser** page.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Construit un objet `CMFCRibbonCustomizeDialog`.|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
  
## <a name="remarks"></a>Notes  
 MFC instancie automatiquement cette classe si vous ne traitez pas le message AFX_WM_ON_RIBBON_CUSTOMIZE, ou si vous retournez 0 à partir du Gestionnaire de message.  
  
 Si vous souhaitez utiliser cette classe dans votre application pour afficher le ruban **personnaliser** boîte de dialogue zone, simplement instancier et appeler le `DoModal` (méthode).  
  
 Étant donné que cette classe est dérivée de [CMFCPropertySheet, classe](../../mfc/reference/cmfcpropertysheet-class.md), vous pouvez ajouter des pages personnalisées en utilisant le `CMFCPropertySheet` API.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxribboncustomizedialog.h  
  
##  <a name="cmfcribboncustomizedialog"></a>  CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog  
 Construit un objet `CMFCRibbonCustomizeDialog`.  
  
```  
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,  
    CMFCRibbonBar* pRibbon);
```  
  
### <a name="parameters"></a>Paramètres  
*pWndParent*<br/>
[in] Pointeur vers la fenêtre parente (généralement le frame principal).  
  
*pRibbon*<br/>
[in] Un pointeur vers le `CMFCRibbonBar` qui doit être personnalisé.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un `CMFCRibbonCustomizeDialog` objet.  
  
 [!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>Notes  
 Le constructeur instancie un [cmfcribboncustomizepropertypage, classe](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) de l’objet et l’ajoute à la collection de pages de feuille de propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
