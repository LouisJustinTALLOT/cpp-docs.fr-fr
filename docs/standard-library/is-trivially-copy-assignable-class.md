---
title: is_trivially_copy_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: 831e7c5afdd39980876a8e8284a68fec2084a4e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413461"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable, classe

Teste si le type a un opérateur d'assignation de copie trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est une classe qui a un copie trivial opérateur d’assignation, sinon, sa valeur est false.

Un constructeur d’assignation pour une classe *T* est trivial s’il est fourni implicitement, la classe *T* n’a aucune fonction virtuelle, la classe *T* n’a aucune bases virtuelles, les classes de tous les membres de données non statiques de type de classe possèdent des opérateurs d’assignation triviaux, et les classes de tous les membres de données non statiques de type tableau de classe possèdent des opérateurs d’assignation triviaux.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
