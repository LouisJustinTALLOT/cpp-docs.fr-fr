---
title: ComPtr::operator ==, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator==
dev_langs:
- C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 703204541a05c260e77562729703677b98fb8e9d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883353"
---
# <a name="comptroperator-operator"></a>ComPtr::operator==, opérateur
Indique si deux objets ComPtr sont égaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool operator==(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator==(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `a`  
 Une référence à un objet ComPtr.  
  
 `b`  
 Une référence à un autre objet ComPtr.  
  
## <a name="return-value"></a>Valeur de retour  
 Premier opérateur rendements `true` si objet `a` est égal à l’objet `b`; sinon, `false`.  
  
 Les deuxième et troisième opérateurs yield `true` si objet `a` est égal à `nullptr`; sinon, `false`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [ComPtr, classe](../windows/comptr-class.md)