---
title: event_receiver | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_receiver
dev_langs:
- C++
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 01ab5aeee7d706da7016cb1ea1f01ff7367de888
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875563"
---
# <a name="eventreceiver"></a>event_receiver
Crée un récepteur d'événements (récepteur).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `type`  
 Une énumération de l’une des valeurs suivantes :  
  
-   `native` pour du code C/C++ non managé (par défaut pour les classes natives).  
  
-   `com` pour le code COM. Cette valeur nécessite que vous incluiez les fichiers d’en-tête suivants :  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout_dependent**  
 Spécifiez *layout_dependent* uniquement si `type` = **com**. *layout_dependent* est une valeur booléenne :  
  
-   **true** signifie que la signature des délégués dans le récepteur doit correspondre exactement à ceux auxquels ils sont raccordés des source de l’événement des événements. Les noms de gestionnaire d’événements récepteur doivent correspondre à ceux spécifiés dans l’interface de source d’événements pertinentes. Vous devez utiliser **coclasse** lorsque *layout_dependent* est **true**. Il est légèrement plus efficace de spécifier **true**.  
  
-   **false** (par défaut) signifie que la classe de stockage et la convention d’appel (virtuelle, statique, etc.) n’est pas nécessaire correspondre à la méthode d’événement et les gestionnaires ; ni d’avez besoin des noms des gestionnaires faire correspondre les noms de méthode interface source d’événements.  
  
## <a name="remarks"></a>Notes  
 Le **event_receiver** attribut C++ Spécifie que la classe ou structure auquel il est appliqué est un récepteur d’événements, à l’aide du modèle d’événement unifié Visual C++.  
  
 **event_receiver** est utilisé avec le [event_source](../windows/event-source.md) attribut et la [__hook](../cpp/hook.md) et [__unhook](../cpp/unhook.md) mots clés. Utilisez **event_source** pour créer des sources d’événements. Utilisez `__hook` dans les méthodes d’un récepteur d’événements pour associer des méthodes de récepteur d’événements (« raccorder ») pour les événements d’une source d’événement. Utilisez `__unhook` pour dissocier les.  
  
 *layout_dependent* est spécifié uniquement pour les récepteurs d’événements COM (`type`=**com**). La valeur par défaut pour *layout_dependent* est **false**.  
  
> [!NOTE]
>  Une classe ou structure modélisée ne peut pas contenir d'événements.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**class**, `struct`|  
|**Renouvelable**|Non|  
|**Attributs requis**|**coclasse** lorsque *layout_dependent*=**true**|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du compilateur](../windows/compiler-attributes.md)   
 [event_source](../windows/event-source.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [Attributs de classe](../windows/class-attributes.md)   
