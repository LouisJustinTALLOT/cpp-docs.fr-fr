---
title: ComPtr::operator&amp; opérateur | Documents Microsoft
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
ms.openlocfilehash: 0bfe8cf9091d888c33420f53f584ca5509d80527
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872404"
---
# <a name="comptroperatoramp-operator"></a>ComPtr::operator&amp; (opérateur)
Libère l’interface associée à ce `ComPtr` de l’objet, puis récupère l’adresse de le `ComPtr` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Une référence faible à actuel `ComPtr`.  
  
## <a name="remarks"></a>Notes  
 Cette méthode diffère [ComPtr::GetAddressOf](../windows/comptr-getaddressof-method.md) dans la mesure où cette méthode libère une référence au pointeur d’interface. Utilisez `ComPtr::GetAddressOf` quand vous exigent l’adresse du pointeur d’interface, mais ne souhaitez pas libérer cette interface.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr, classe](../windows/comptr-class.md)