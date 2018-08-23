---
title: Comptr::getaddressof, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 972a41d0-c2ef-4ae3-b2cd-77cc45156ac9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98609ce9cc15940586d626c52d24b5ca506164e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598992"
---
# <a name="comptrgetaddressof-method"></a>ComPtr::GetAddressOf, méthode

Récupère l’adresse de la [ptr_](../windows/comptr-ptr-data-member.md) membre de données, qui contient un pointeur vers l’interface représentée par ce **ComPtr**.

## <a name="syntax"></a>Syntaxe

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

## <a name="return-value"></a>Valeur de retour

L’adresse d’une variable.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ComPtr, classe](../windows/comptr-class.md)