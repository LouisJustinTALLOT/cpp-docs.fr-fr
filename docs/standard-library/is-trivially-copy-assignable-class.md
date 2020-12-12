---
description: 'En savoir plus sur : classe is_trivially_copy_assignable'
title: is_trivially_copy_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: 010e820db570f594568cb60f4edae83b91a997c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271237"
---
# <a name="is_trivially_copy_assignable-class"></a>is_trivially_copy_assignable, classe

Teste si le type a un opérateur d'assignation de copie trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est une classe qui a un opérateur d’assignation de copie trivial. sinon, sa valeur est false.

Un constructeur d’assignation pour une classe *t* est trivial s’il est fourni implicitement, la classe *t* n’a pas de fonctions virtuelles, la classe *t* n’a aucune base virtuelle, les classes de tous les membres de données non statiques de type classe ont des opérateurs d’assignation trivial, et les classes de tous les membres de données non statiques de type tableau de classe ont des opérateurs d’assignation

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
