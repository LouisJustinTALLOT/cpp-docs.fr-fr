---
description: 'En savoir plus sur : classe is_nothrow_default_constructible'
title: is_nothrow_default_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
ms.openlocfilehash: bbfadf10048175472c10f264856cdb519896b65f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230794"
---
# <a name="is_nothrow_default_constructible-class"></a>is_nothrow_default_constructible, classe

Teste si le type a un constructeur par défaut qui ne lève pas d'exception.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* a un constructeur par défaut nothrow. sinon, sa valeur est false. Une instance du prédicat de type équivaut à `is_nothrow_constructible<Ty>`.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
