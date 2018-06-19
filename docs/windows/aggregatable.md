---
title: peut être agrégé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.aggregatable
dev_langs:
- C++
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1d80b2fb707145f698e8d9bb883059478c3da10b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863824"
---
# <a name="aggregatable"></a>aggregatable
Indique que la classe prend en charge l’agrégation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ aggregatable(   
   value  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *valeur* (facultatif)  
 Un paramètre pour indiquer quand l’objet COM peut être agrégée :  
  
-   **jamais** l’objet COM ne peut pas être agrégée.  
  
-   **autorisé** l’objet COM peut être créée directement, ou il peut être agrégé. Il s'agit de la valeur par défaut.  
  
-   **toujours** l’objet COM ne peut pas être créé directement et peuvent uniquement être agrégée. Lorsque vous appelez `CoCreateInstance` pour cet objet, vous devez spécifier l’objet d’agrégation **IUnknown** interface (le contrôle **IUnknown**).  
  
## <a name="remarks"></a>Notes  
 Le **peuvent être agrégées** attribut C++ a les mêmes fonctionnalités que le [peuvent être agrégées](http://msdn.microsoft.com/library/windows/desktop/aa366721) attribut MIDL. Cela signifie que le compilateur passe le **peuvent être agrégées** par le biais d’attributs dans le fichier .idl généré.  
  
 Cet attribut exige que l’attribut [coclass](../windows/coclass.md), [progid](../windows/progid.md)ou [vi_progid](../windows/vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si **progid** est appliqué, **vi_progid** et **coclass** sont également appliqués.  
  
 **Projets ATL**  
  
 Si vous utilisez cet attribut dans un projet qui utilise ATL, le comportement de l’attribut change. En plus du comportement décrit précédemment, l’attribut ajoute également une des macros suivantes à la classe cible :  
  
|Valeur de paramètre|Macro inséré|  
|---------------------|--------------------|  
|**Jamais**|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|  
|**Autorisé**|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|  
|**Toujours**|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|  
  
## <a name="example"></a>Exemple  
  
```  
// cpp_attr_ref_aggregatable.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="MyModule")];  
  
[ coclass, aggregatable(allowed),  
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]  
class CMyClass {};  
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
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Aggregation](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
