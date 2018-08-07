---
title: iid_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0f0dd12df088d8fc55cc4f1a8eaf71bcbb7d4e93
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603288"
---
# <a name="iidis"></a>iid_is
Spécifie l’IID de l’interface COM vers laquelle pointé un pointeur d’interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ iid_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression*  
 Une expression de langage C qui spécifie un IID d’une interface COM vers laquelle pointe un pointeur d’interface.  
  
## <a name="remarks"></a>Notes  
 Le **iid_is** attribut C++ a les mêmes fonctionnalités que le [iid_is](http://msdn.microsoft.com/library/windows/desktop/aa367044) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant illustre l’utilisation de **iid_is**:  
  
```cpp  
// cpp_attr_ref_iid_is.cpp  
// compile with: /LD  
#include "wtypes.h"  
#include "unknwn.h"  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]   
   IUnknown ** ppvObject);  
};  
  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Paramètre d’interface, membre de données|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de paramètres](../windows/parameter-attributes.md)   