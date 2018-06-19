---
title: ComPtrRef::operator ! =, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
dev_langs:
- C++
ms.assetid: ab3093cc-6fbd-4039-890a-6df1cde992b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d5a6e7389215452177add30b587004c312aeae1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883552"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!=, opérateur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator!=(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `a`  
 Une référence à un objet ComPtrRef.  
  
 `b`  
 Une référence à un autre objet ComPtrRef, ou un pointeur vers un objet anonyme (`void*`).  
  
## <a name="return-value"></a>Valeur de retour  
 Premier opérateur rendements `true` si objet `a` n’est pas égal à l’objet `b`; sinon, `false`.  
  
 Les deuxième et troisième opérateurs yield `true` si objet `a` n’est pas égal à `nullptr`; sinon, `false`.  
  
 Les opérateurs quatrième et cinquième yield `true` si objet `a` n’est pas égal à l’objet `b`; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Indique si deux objets ComPtrRef ne sont pas égaux.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl::Details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef, classe](../windows/comptrref-class.md)