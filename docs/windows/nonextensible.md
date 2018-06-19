---
title: nonextensible | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87cdbf66676ed2a3e6054006270b39ad80325857
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881599"
---
# <a name="nonextensible"></a>nonextensible
Spécifie que le `IDispatch` implémentation inclut uniquement les propriétés et méthodes répertoriées dans la description de l’interface et ne peuvent pas être étendus avec des membres supplémentaires au moment de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[nonextensible]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **nonextensible** attribut C++ a les mêmes fonctionnalités que le [nonextensible](http://msdn.microsoft.com/library/windows/desktop/aa367120) attribut MIDL.  
  
 Utilisation de **nonextensible** requiert également le [oleautomation](../windows/oleautomation.md) attribut.  
  
## <a name="example"></a>Exemple  
 Le code suivant illustre une utilisation de la **nonextensible** attribut :  
  
```  
// cpp_attr_ref_nonextensible.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export] typedef long HRESULT;  
  
[dual, nonextensible, ms_union, oleautomation,   
uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   HRESULT procedure (int i);   
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|`interface`|  
|**Renouvelable**|Non|  
|**Attributs requis**|**Double** et **oleautomation**, ou **dispinterface**|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
