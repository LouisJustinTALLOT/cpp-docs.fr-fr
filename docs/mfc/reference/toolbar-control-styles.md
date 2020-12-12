---
description: En savoir plus sur les styles de contrôle ToolBar
title: Styles de contrôle ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
ms.openlocfilehash: b044f353ddbdc4ccc9d5050ea14307386b7c2a15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218717"
---
# <a name="toolbar-control-styles"></a>Styles de contrôle ToolBar

La [classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) possède un ensemble d’indicateurs de style qui déterminent l’apparence et le comportement du bouton. Vous pouvez définir une combinaison de ces indicateurs en appelant [CMFCToolBarButton :: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Cette rubrique répertorie les valeurs d’indicateur de style et leurs significations.

## <a name="property-values"></a>Valeurs de la propriété

Les valeurs suivantes déterminent le type de bouton que le contrôle représente :

|Nom|Description|
|-|-|
|TBBS_BUTTON|Bouton de bouton standard (par défaut).  |
|TBBS_CHECKBOX|Case à cocher.  |
|TBBS_CHECKGROUP|Début d’un groupe de cases à cocher.  |
|TBBS_GROUP|Début d’un groupe de boutons.  |
|TBBS_SEPARATOR|Séparateur.  |

Les valeurs suivantes représentent l’état actuel du contrôle :

|Nom|Description|
|-|-|
|TBBS_CHECKED|Case à cocher est activée.  |
|TBBS_DISABLED|Le contrôle est désactivé.  |
|TBBS_INDETERMINATE|La case à cocher est dans un état indéterminé.  |
|TBBS_PRESSED|Le bouton est enfoncé.  |

La valeur suivante modifie la disposition du bouton dans la barre d’outils :

|Nom|Description|
|-|-|
|TBBS_BREAK|Place l’élément sur une nouvelle ligne ou dans une nouvelle colonne sans séparer les colonnes.  |

## <a name="remarks"></a>Notes

Le style actuel est stocké dans [CMFCToolBarButton :: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Ne définissez pas une nouvelle valeur                 `m_nStyle` directement, car certaines classes dérivées effectuent un traitement supplémentaire lorsque vous appelez `SetStyles` .

Le gestionnaire visuel détermine l’apparence des boutons dans chaque État. Pour plus d’informations, consultez le [Gestionnaire de visualisation](../../mfc/visualization-manager.md) .

## <a name="requirements"></a>Spécifications

**En-tête :** afxtoolbarbutton. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Gestionnaire de visualisation](../../mfc/visualization-manager.md)
