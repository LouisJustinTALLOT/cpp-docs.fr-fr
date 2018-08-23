---
title: back_inserter, fonction | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
dev_langs:
- C++
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6142255c00d9764e4a1a18dab094899b5e9d9e1d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589985"
---
# <a name="backinserter-function"></a>back_inserter (fonction)
Retourne un itérateur qui est utilisé pour insérer des éléments à la fin de la collection spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template <typename T>
Platform::BackInsertIterator<T>   
    back_inserter(IVector<T>^ v);  
  
template<typename T>  
Platform::BackInsertIterator<T>   
   back_inserter(IObservableVector<T>^ v);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Paramètre de type de modèle.  
  
 `v`  
 Pointeur d’interface qui permet d’accéder à la collection sous-jacente.  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur.  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** collection.h  
  
 **Espace de noms :** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Voir aussi  
 [Windows::Foundation :: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)