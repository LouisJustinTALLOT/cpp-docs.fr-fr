---
title: Classe de CMFCCustomColorsPropertyPage | Documents Microsoft
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
ms.openlocfilehash: 8123db8e4a8dfba94e469881af8fbb2ecb40e2a0
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041979"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Classe de CMFCCustomColorsPropertyPage
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
 La `CMFCColorDialog` classe utilise cette classe pour afficher la page de propriété de couleur personnalisée. Pour plus d’informations sur `CMFCColorDialog`, consultez [CMFCColorDialog classe](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un `CMFCCustomColorsPropertyPage` de l’objet et les composants de couleur de la page de propriétés.  
  
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
|[in] *R*|La composante rouge de la valeur RVB.|  
|[in] *G*|La composante verte de la valeur RVB.|  
|[in] *B*|La composante bleue de la valeur RVB.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode met à jour le RVB actuel et TSL (teinte, luminosité et saturation) couleur valeurs associées de la page de propriétés. Le [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) méthode appelle cette méthode lorsque le framework initialise la boîte de dialogue couleur ou l’utilisateur appuie sur le bouton gauche de la souris. Pour plus d’informations sur `CMFCColorDialog`, consultez [CMFCColorDialog classe](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage, classe](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
