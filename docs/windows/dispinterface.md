---
title: dispinterface | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.dispinterface
dev_langs: C++
helpviewer_keywords: dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e52d050b9b05ccb72969c531297367e729c258b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="dispinterface"></a>dispinterface
Place une interface dans le fichier .idl comme interface de dispatch.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[dispinterface]  
  
```  
  
## <a name="remarks"></a>Remarques  
 Quand l’attribut C++ **dispinterface** précède une interface, il fait en sorte qu’elle soit placée dans le bloc de bibliothèque dans le fichier .idl généré.  
  
 Une interface de dispatch dérivent de `IDispatch`, sauf si vous spécifiez une classe de base. Vous devez spécifier un [id](../windows/id.md) pour les membres d’une interface de dispatch.  
  
 L’exemple d’utilisation de [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) dans la documentation MIDL :  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 n’est pas valide pour l’attribut **dispinterface** .  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple montrant comment utiliser [dispinterface](../windows/bindable.md) , consultez l’exemple de **bindable**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|`interface`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|**dual**, **object**, **oleautomation**, `local`, **ms_union**|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs par utilisation](../windows/attributes-by-usage.md)   
 [UUID](../windows/uuid-cpp-attributes.md)   
 [Double](../windows/dual.md)   
 [personnalisé](../windows/custom-cpp.md)   
 [object](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   
