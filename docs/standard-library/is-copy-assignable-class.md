---
description: 'En savoir plus sur : classe is_copy_assignable'
title: is_copy_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_copy_assignable
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
ms.openlocfilehash: f13752ce74f316f180fb874572efaf15d1c06c31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323796"
---
# <a name="is_copy_assignable-class"></a>is_copy_assignable, classe

Teste si le type peut être copié lors de l'assignation.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est une classe qui a un opérateur d’assignation de copie. sinon, sa valeur est false. Équivalent à is_assignable \<Ty&, const Ty&> .

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
