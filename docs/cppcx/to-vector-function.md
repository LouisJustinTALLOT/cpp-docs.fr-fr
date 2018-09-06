---
title: to_vector, fonction | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
dev_langs:
- C++
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00ecb00a890629c69994019c9232ff559ea93c96
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758872"
---
# <a name="tovector-function"></a>to_vector (fonction)
Retourne un `std::vector` dont la valeur est la même que la collection sous-jacente du paramètre IVector ou IVectorView spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
inline ::std::vector<T> to_vector(IVector<T>^ v); 
 
template <typename T>  
inline ::std::vector<T> to_vector(IVectorView<T>^ v);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Paramètre de type de modèle.  
  
 `v`  
 Interface IVector ou IVectorView qui permet d'accéder à un objet Vector ou VectorView sous-jacent.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** collection.h  
  
 **Espace de noms :** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Voir aussi  
 [Windows::Foundation :: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)