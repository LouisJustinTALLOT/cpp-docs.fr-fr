---
title: Cmfccustomcolorspropertypage, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
dev_langs:
- C++
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c8fea125c61bebe836a31c0b2718741e8c531d3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716852"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Cmfccustomcolorspropertypage, classe
Représente une page de propriétés que vous pouvez sélectionner des couleurs personnalisées dans une boîte de dialogue couleur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Constructeur par défaut.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|`CMFCCustomColorsPropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|`CMFCCustomColorsPropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Définit les composants de couleur de la page de propriétés.|  
  
### <a name="remarks"></a>Notes  
 Le `CMFCColorDialog` utilise cette classe pour afficher la page de propriété de couleur personnalisée. Pour plus d’informations sur `CMFCColorDialog`, consultez [cmfccolordialog, classe](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un `CMFCCustomColorsPropertyPage` de l’objet et définir les composants de couleur de la page de propriétés.  
  
 [!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcustomcolorspropertypage.h  
  
##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup  
 Définit les composants de couleur de la page de propriétés.  
  
```  
void Setup(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|*R*|[in] Le composant rouge de la valeur RVB.|  
|*G*|[in] Le composant vert de la valeur RVB.|  
|*B*|[in] La composante bleue de la valeur RVB.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode met à jour le RVB actuel et TSL (teinte, luminosité et saturation) couleur valeurs associées de la page de propriétés. Le [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) méthode appelle cette méthode lorsque le framework initialise la boîte de dialogue couleur ou l’utilisateur appuie sur le bouton gauche de la souris. Pour plus d’informations sur `CMFCColorDialog`, consultez [cmfccolordialog, classe](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Cmfccolordialog, classe](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage, classe](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
