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
ms.openlocfilehash: f513ac83e0ee83109f42cf87b80b4fcc4960db1f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598601"
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