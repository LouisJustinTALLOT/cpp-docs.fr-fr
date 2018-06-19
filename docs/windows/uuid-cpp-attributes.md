---
title: UUID (attributs C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e56793855b278e0631c39ebfcdc51669a001a24b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891530"
---
# <a name="uuid-c-attributes"></a>uuid (attributs C++)
Spécifie l’ID unique pour une classe ou interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ uuid(  
   "uuid"  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *uuid*  
 Identificateur unique de 128 bits.  
  
## <a name="remarks"></a>Notes  
 Si la définition d’une interface ou une classe ne spécifie pas le `uuid` attribut C++, puis le compilateur Visual C++ fournit une. Lorsque vous spécifiez un `uuid`, vous devez inclure les guillemets.  
  
 Si vous ne spécifiez pas `uuid`, le compilateur génère le même GUID pour les interfaces ou classes portant le même nom dans les projets autre attribut sur un ordinateur.  
  
 Vous pouvez utiliser Uuidgen.exe ou Guidgen.exe pour générer votre propre ID unique. (Pour exécuter un de ces outils, cliquez sur **Démarrer** et cliquez sur **exécuter** dans le menu. Entrez le nom de l’outil requis.)  
  
 Lorsqu’il est utilisé dans un projet qui n’utilise pas également ATL, en spécifiant le `uuid` attribut est identique à la [uuid](../cpp/uuid-cpp.md) __declspec (modificateur). Pour récupérer le `uuid` d’une classe, vous pouvez utiliser [__uuidof](../cpp/uuidof-operator.md)  
  
## <a name="example"></a>Exemple  
 Consultez le [pouvant être liés](../windows/bindable.md) exemple pour un exemple d’utilisation de `uuid`.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, `struct`, `interface`, **union**, `enum`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)   
