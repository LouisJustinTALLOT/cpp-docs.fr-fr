---
title: Interfacetraits::casttobase, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 473656f25c4ba08e011bef8f938cea54bdc51d6d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424898"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de paramètre *ptr*.

*ptr*<br/>
Pointeur vers un type *T*.

## <a name="return-value"></a>Valeur de retour

Un pointeur vers `Base`.

## <a name="remarks"></a>Notes

Effectue un cast du pointeur spécifié vers un pointeur vers `Base`.

Pour plus d’informations sur `Base`, consultez la section Typedefs publics dans [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[InterfaceTraits, structure](../windows/interfacetraits-structure.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)