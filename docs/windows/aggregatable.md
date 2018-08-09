---
title: peut être agrégé | Microsoft Docs
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
ms.openlocfilehash: 2b18f4c38777076357170540e35fc5515025e126
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643005"
---
# <a name="aggregatable"></a>aggregatable
Indique que la classe prend en charge l’agrégation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ aggregatable(   
   value  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *valeur* (facultatif)  
 Un paramètre pour indiquer quand l’objet COM peut être agrégée :  
  
-   `never` L’objet COM ne peut pas être agrégée.  
  
-   `allowed` L’objet COM peut être créé directement, ou il peut être agrégé. Il s'agit de la valeur par défaut.  
  
-   `always` L’objet COM ne peut pas être créé directement et peut uniquement être agrégée. Lorsque vous appelez `CoCreateInstance` pour cet objet, vous devez spécifier l’objet d’agrégation `IUnknown` interface (le contrôle `IUnknown`).  
  
## <a name="remarks"></a>Notes  
 Le **agrégeable** attribut C++ a les mêmes fonctionnalités que le [agrégeable](http://msdn.microsoft.com/library/windows/desktop/aa366721) attribut MIDL. Cela signifie que le compilateur passe le **agrégeable** par le biais d’attributs dans le fichier .idl généré.  
  
 Cet attribut exige que l’attribut [coclass](../windows/coclass.md), [progid](../windows/progid.md)ou [vi_progid](../windows/vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliquée, `vi_progid` et `coclass` sont également appliquées.  
  
### <a name="atl-projects"></a>Projets ATL  
  
 Si vous utilisez cet attribut dans un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement décrit précédemment, l’attribut ajoute également une des macros suivantes à la classe cible :  
  
|Valeur de paramètre|Macro inséré|  
|---------------------|--------------------|  
|`Never`|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|  
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|  
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|  
  
## <a name="example"></a>Exemple  
  
```cpp  
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
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **struct**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Un ou plusieurs des opérations suivantes : `coclass`, `progid`, ou `vi_progid`.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Aggregation](http://msdn.microsoft.com/library/windows/desktop/ms686558)   