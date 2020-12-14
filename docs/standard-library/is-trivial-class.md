---
description: 'En savoir plus sur : classe is_trivial'
title: is_trivial, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 56e5a3c915893b88228f4a40307d2c1e3c32555d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247655"
---
# <a name="is_trivial-class"></a>is_trivial, classe

Teste si le type est un type trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type trivial. sinon, sa valeur est false. Les types triviaux sont les types scalaires, les types de classes pouvant être copiés de façon triviale, les tableaux de ces types et les versions cv-qualified de ces types.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
