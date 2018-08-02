---
title: ComPtr::operator&amp; opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0afff1699a4c7a3a14f07967cfb5ba5727ba0320
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461560"
---
# <a name="comptroperatoramp-operator"></a>ComPtr::operator&amp; opérateur
Libère l’interface associée à cet **ComPtr** de l’objet, puis récupère l’adresse de la **ComPtr** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Une référence faible à actuel **ComPtr**.  
  
## <a name="remarks"></a>Notes  
 Cette méthode diffère de [ComPtr::GetAddressOf](../windows/comptr-getaddressof-method.md) dans la mesure où cette méthode libère une référence au pointeur d’interface. Utilisez `ComPtr::GetAddressOf` lorsque vous nécessitent l’adresse du pointeur d’interface, mais ne souhaitez pas libérer cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr, classe](../windows/comptr-class.md)