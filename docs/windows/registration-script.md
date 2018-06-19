---
title: registration_script | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.registration_script
dev_langs:
- C++
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4385dd12fccafb154a637dd5260764667d3887a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878721"
---
# <a name="registrationscript"></a>registration_script
Exécute le script d’inscription personnalisé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ registration_script(   
   script   
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *script*  
 Le chemin d’accès complet à un fichier de script (.rgs) d’inscription personnalisé. La valeur **aucun**, tel que `script = "none"`, indique ne qu’aucune configuration requise de l’inscription de la coclasse.  
  
## <a name="remarks"></a>Notes  
 Le **registration_script** attribut C++ exécute le script d’inscription personnalisé spécifié par **script**. Si cet attribut n’est pas spécifié, un fichier .rgs standard (contenant des informations pour l’enregistrement du composant) est utilisé. Pour plus d’informations sur les fichiers .rgs, consultez [le composant de Registre ATL (inscription)](../atl/atl-registry-component-registrar.md).  
  
 Cet attribut exige que l’attribut [coclass](../windows/coclass.md), [progid](../windows/progid.md)ou [vi_progid](../windows/vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément.  
  
## <a name="example"></a>Exemple  
 Le code suivant spécifie que le composant a un script de Registre appelé cpp_attr_ref_registration_script.rgs.  
  
```  
// cpp_attr_ref_registration_script.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="REG")];  
  
[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]  
__interface IFace {};  
  
// requires "cpp_attr_ref_registration_script.rgs"  
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist  
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),  
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]  
class CMyClass:public IFace {};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**class**, `struct`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Un ou plusieurs des éléments suivants : **coclass**, **progid**ou **vi_progid**.|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs COM](../windows/com-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [rdx](../windows/rdx.md)   
