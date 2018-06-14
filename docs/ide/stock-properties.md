---
title: Propriétés stock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- stock properties, about stock properties
- stock properties
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3586fb33c30148c870b096d0d49a41d7ad8c6c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335432"
---
# <a name="stock-properties"></a>Propriétés stock
Si vous ajoutez une propriété à une dispinterface MFC à l’aide de [l’Assistant Ajout de propriété](../ide/idl-attributes-add-property-wizard.md), vous pouvez choisir une propriété stock dans la liste **Nom de la propriété** de la page [Noms](../ide/names-add-property-wizard.md) de l’Assistant. Ces propriétés sont les suivantes :  
  
|Nom de propriété|Description|  
|-------------------|-----------------|  
|**Appearance**|Retourne ou définit une valeur qui détermine l’apparence du contrôle. La propriété **Appearance** du contrôle peut inclure ou omettre les effets 3D. Il s’agit d’une propriété ambiante en lecture/écriture.|  
|`BackColor`|Retourne ou définit la propriété `BackColor` ambiante du contrôle avec une couleur de palette (RVB) ou une couleur système prédéfinie. Par défaut, sa valeur correspond à la couleur de premier plan du conteneur du contrôle. Il s’agit d’une propriété ambiante en lecture/écriture.|  
|`BorderStyle`|Retourne ou définit le style de bordure d’un contrôle. Il s’agit d’une propriété en lecture/écriture.|  
|**Légende**|Retourne ou définit la propriété **Caption** du contrôle. La légende est le titre de la fenêtre. **Caption** n’a pas de type d’implémentation **Variable membre**.|  
|**Activé**|Retourne ou définit la propriété **Enabled** du contrôle. Un contrôle activé peut répondre aux événements générés par l’utilisateur.|  
|**Police**|Retourne ou définit la police ambiante du contrôle. Null si le contrôle n’a pas de police.|  
|`ForeColor`|Retourne ou définit la propriété `ForeColor` ambiante du contrôle.|  
|**hWnd**|Retourne ou définit la propriété **hWnd** du contrôle. **hWnd** n’a pas de type d’implémentation **Variable membre**.|  
|**ReadyState**|Retourne ou définit la propriété **ReadyState** du contrôle. Un contrôle peut être non initialisé, initialisé, en cours de chargement, interactif ou complet. Pour plus d’informations, consultez [READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx) dans le *kit SDK Internet*.|  
|**Text**|Retourne ou définit le texte présent dans un contrôle. **Text** n’a pas de type d’implémentation **Variable membre**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une propriété](../ide/adding-a-property-visual-cpp.md)   
 [Attributs IDL, Assistant Ajout de propriété](../ide/idl-attributes-add-property-wizard.md)