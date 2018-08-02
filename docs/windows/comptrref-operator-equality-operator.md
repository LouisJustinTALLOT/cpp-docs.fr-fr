---
title: ComPtrRef::operator ==, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs:
- C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 606059712e60ba181998155b55ae02ba8b27c4da
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463952"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator==, opérateur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator==(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *a*  
 Une référence à un objet ComPtrRef.  
  
 *b*  
 Une référence à un autre objet ComPtrRef, ou un pointeur vers un type anonyme (`void*`).  
  
## <a name="return-value"></a>Valeur de retour  
 Le premier produit opérateur **true** si objet *un* est égal à l’objet *b*; sinon, **false**.  
  
 Les deuxième et troisième opérateurs yield **true** si objet *un* est égal à **nullptr**; sinon, **false**.  
  
 Les quatrième et cinquième opérateurs yield **true** si objet *un* est égal à l’objet *b*; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Indique si deux objets ComPtrRef sont égaux.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl::Details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef, classe](../windows/comptrref-class.md)