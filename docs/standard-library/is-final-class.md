---
description: 'En savoir plus sur : classe is_final'
title: is_final, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_final
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
ms.openlocfilehash: 04660309205689e14200cb5d214ce5dc80efb88f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323739"
---
# <a name="is_final-class"></a>is_final, classe

Teste si le type est un type de classe marqué `final`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type de classe marqué `final` ; sinon, sa valeur est false. Si *T* est un type de classe, il doit s’agir d’un type complet.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Spécificateur final](../cpp/final-specifier.md)
