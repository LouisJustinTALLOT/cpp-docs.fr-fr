---
title: Styles de contrôle de barre d’outils | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1958c83ef5a0eec5f3c7f5873451edd3839146be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373193"
---
# <a name="toolbar-control-styles"></a>Styles de contrôle ToolBar
[Classe de CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) possède un ensemble d’indicateurs de style qui déterminent l’apparence et comportement du bouton. Vous pouvez définir une combinaison de ces indicateurs en appelant [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Cette rubrique répertorie les valeurs d’indicateur de style et leurs significations.  
  
## <a name="property-values"></a>Valeurs de propriété  
 Les valeurs suivantes déterminent le type de bouton qui représente le contrôle :  
  
 TBBS_BUTTON  
 Bouton de commande standard (valeur par défaut).  
  
 TBBS_CHECKBOX  
 case à cocher.  
  
 TBBS_CHECKGROUP  
 Le début d’un groupe de cases à cocher.  
  
 TBBS_GROUP  
 Le début d’un groupe de boutons.  
  
 TBBS_SEPARATOR  
 Séparateur.  
  
 Les valeurs suivantes représentent l’état actuel du contrôle :  
  
 TBBS_CHECKED  
 Case à cocher est activée.  
  
 TBBS_DISABLED  
 Le contrôle est désactivé.  
  
 TBBS_INDETERMINATE  
 Case à cocher est dans un état indéterminé.  
  
 TBBS_PRESSED  
 Bouton est enfoncé.  
  
 La valeur suivante modifie la disposition du bouton dans la barre d’outils :  
  
 TBBS_BREAK  
 Place l’élément sur une nouvelle ligne ou dans une nouvelle colonne sans séparation des colonnes.  
  
## <a name="remarks"></a>Notes  
 Le style actuel est stocké dans [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Ne définissez pas une nouvelle valeur dans `m_nStyle` directement, car certaines classes dérivées effectuent un traitement supplémentaire lorsque vous appelez `SetStyles`.  
  
 Le Gestionnaire visuel détermine l’apparence des boutons dans chaque état. Consultez [Gestionnaire de visualisation](../../mfc/visualization-manager.md) pour plus d’informations.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxtoolbarbutton.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)   
 [Classe de CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Gestionnaire de visualisation](../../mfc/visualization-manager.md)


