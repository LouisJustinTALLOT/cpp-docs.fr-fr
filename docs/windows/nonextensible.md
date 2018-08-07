---
title: nonextensible | Microsoft Docs
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
ms.openlocfilehash: 2f670da3ad4858f3c09903f2ed3ec6aa58268180
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608493"
---
# <a name="nonextensible"></a>nonextensible
Spécifie que le `IDispatch` implémentation inclut uniquement les propriétés et méthodes répertoriées dans la description de l’interface et ne peut pas être étendus avec des membres supplémentaires en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[nonextensible]  
```  
  
## <a name="remarks"></a>Notes  
 Le **nonextensible** attribut C++ a les mêmes fonctionnalités que le [nonextensible](http://msdn.microsoft.com/library/windows/desktop/aa367120) attribut MIDL.  
  
 Utilisation de **nonextensible** requiert également le [oleautomation](../windows/oleautomation.md) attribut.  
  
## <a name="example"></a>Exemple  
 Le code suivant illustre une utilisation de la **nonextensible** attribut :  
  
```cpp  
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
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**interface**|  
|**Renouvelable**|Non|  
|**Attributs requis**|`dual` et `oleautomation`, ou `dispinterface`|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   