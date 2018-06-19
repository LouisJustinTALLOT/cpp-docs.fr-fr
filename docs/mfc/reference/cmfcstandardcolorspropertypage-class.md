---
title: Classe de CMFCStandardColorsPropertyPage | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abaad4870354ba331e615e0739dc7526dd39607d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374278"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>Classe de CMFCStandardColorsPropertyPage
Représente une page de propriétés qui utilisent des utilisateurs à sélectionner des couleurs standards dans une boîte de dialogue couleur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCStandardColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Constructeur par défaut.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|`CMFCStandardColorsPropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|`CMFCStandardColorsPropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
  
### <a name="remarks"></a>Notes  
 La `CMFCColorDialog` classe utilise cette classe pour afficher la page de propriété de couleur standard. Pour plus d’informations sur `CMFCColorDialog`, consultez [CMFCColorDialog classe](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxstandardcolorspropertypage.h  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCCustomColorsPropertyPage, classe](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
