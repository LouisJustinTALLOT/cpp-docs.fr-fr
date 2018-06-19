---
title: ComPtr::operator =, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f4066db37de8a993802970784f09141352fef028
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871199"
---
# <a name="comptroperator-operator"></a>ComPtr::operator=, opérateur
Assigne une valeur au ComPtr actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <typename U>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `U`  
 Une classe.  
  
 `other`  
 Une référence de pointeur, référence ou rvalue à un type ou un autre ComPtr.  
  
## <a name="return-value"></a>Valeur de retour  
 Une référence au ComPtr actuel.  
  
## <a name="remarks"></a>Notes  
 La première version de cet opérateur assigne une valeur vide pour le ComPtr actuel.  
  
 Dans la deuxième version, si le pointeur d’interface affectation n’est pas le même que le pointeur d’interface ComPtr actuel, le second pointeur d’interface est attribué au ComPtr actuel.  
  
 Dans la troisième version, le pointeur d’interface affectation est assigné au ComPtr actuel.  
  
 Dans la quatrième version, si le pointeur d’interface de la valeur d’assignation n’est pas le même que le pointeur d’interface ComPtr actuel, le second pointeur d’interface est attribué au ComPtr actuel.  
  
 La cinquième version est un opérateur de copie ; une référence à un ComPtr est assignée au ComPtr actuel.  
  
 La sixième version est un opérateur de copie qui utilise la sémantique ; de déplacement une référence rvalue à un ComPtr si n’importe quel type est statique effectué, puis affecté au ComPtr actuel.  
  
 La septième version est un opérateur de copie qui utilise la sémantique ; de déplacement une référence rvalue à un ComPtr de type `U` est statique effectué puis et affecté au ComPtr actuel.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr, classe](../windows/comptr-class.md)