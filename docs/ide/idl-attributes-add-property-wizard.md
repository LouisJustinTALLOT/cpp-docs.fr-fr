---
title: Attributs IDL, Assistant Ajout de propriété | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12fee7eadecbd81e3c4e410d254de50bcf3a9ac0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208824"
---
# <a name="idl-attributes-add-property-wizard"></a>Attributs IDL, Assistant Ajout de propriété
Utilisez cette page de l’Assistant Ajout de propriété pour spécifier tous les paramètres IDL (Interface Definition Language) de la propriété.  
  
 **ID**  
 Définit l’ID numérique qui identifie la propriété. Cette option n’est pas disponible pour les propriétés des interfaces personnalisées. Consultez [id](/windows/desktop/Midl/id) dans les *Informations de référence MIDL*.  
  
 **helpcontext**  
 Spécifie un ID de contexte qui permet à l’utilisateur de voir des informations sur cette propriété dans le fichier d’aide. Consultez [helpcontext](/windows/desktop/Midl/helpcontext) dans les *Informations de référence MIDL*.  
  
 **helpstring**  
 Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique. Par défaut, elle est définie sur « property *Nom de la propriété* ». Consultez [helpstring](/windows/desktop/Midl/helpstring) dans les *Informations de référence MIDL*.  
  
## <a name="other-options"></a>Autres options  
 Les options ne sont pas toutes disponibles pour tous les types de propriété.  
  
|Option|Description|  
|------------|-----------------|  
|**bindable**|Indique que la propriété prend en charge la liaison de données. Consultez [bindable](/windows/desktop/Midl/bindable) dans les *Informations de référence MIDL*. Pour l’implémentation stock de la propriété, cette option est définie par défaut et n’est pas modifiable.|  
|**defaultbind**|Indique la seule propriété prenant en charge la liaison de données qui représente le mieux l’objet. Consultez [defaultbind](/windows/desktop/Midl/defaultbind) dans les *Informations de référence MIDL*.|  
|**displaybind**|Indique que cette propriété doit être montrée à l’utilisateur comme pouvant être liée. Consultez [displaybind](/windows/desktop/Midl/displaybind) dans les *Informations de référence MIDL*.|  
|**immediatebind**|Indique que la base de données est immédiatement avertie de tout changement de cette propriété d’un objet lié aux données. Consultez [immediatebind](/windows/desktop/Midl/immediatebind) dans les *Informations de référence MIDL*.|  
|**defaultcollelem**|Indique que la propriété est une fonction d’accesseur pour un élément de la collection par défaut. Consultez [defaultcollelem](/windows/desktop/Midl/defaultcollelem) dans les *Informations de référence MIDL*.|  
|**nonbrowsable**|Marque un membre d’interface ou de dispinterface qui ne doit pas être affiché dans un navigateur de propriétés. Consultez [nonbrowsable](/windows/desktop/Midl/nonbrowsable) dans les *Informations de référence MIDL*.|  
|**requestedit**|Indique que la propriété prend en charge la notification **OnRequestEdit**. Consultez [requestedit](/windows/desktop/Midl/requestedit) dans les *Informations de référence MIDL*. Pour l’implémentation stock de la propriété, cette option est définie par défaut et n’est pas modifiable.|  
|**source**|Indique qu’un membre de la propriété est une source d’événements. Consultez [source](/windows/desktop/Midl/source) dans les *Informations de référence MIDL*.|  
|**hidden**|Indique que la propriété existe, mais qu’elle ne doit pas être affichée dans un navigateur orienté utilisateur. Consultez [hidden](/windows/desktop/Midl/hidden) dans les *Informations de référence MIDL*.|  
|**restricted**|Spécifie que la propriété ne peut pas être appelée arbitrairement. Consultez [restricted](/windows/desktop/Midl/restricted) dans les *Informations de référence MIDL*.|  
|`local`|Spécifie au compilateur MIDL que la propriété n’est pas distante. Consultez [local](/windows/desktop/Midl/local) dans les *Informations de référence MIDL*.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une propriété](../ide/adding-a-property-visual-cpp.md)   
 [Noms, Assistant Ajout de propriété](../ide/names-add-property-wizard.md)   
 [Implémentation d’une interface](../ide/implementing-an-interface-visual-cpp.md)   
 [Propriétés stock](../ide/stock-properties.md)