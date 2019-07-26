---
title: is_trivially_move_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: 279da956eaff21c39c6e5ca563f26989105f7e74
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448363"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible, classe

Teste si le type a un constructeur de déplacement trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est une classe qui a un constructeur de déplacement trivial. sinon, sa valeur est false.

Un constructeur de déplacement pour une classe *Ty* est trivial si:

il est déclaré implicitement ;

ses types de paramètres sont équivalents à ceux d'une déclaration implicite ;

la classe *Ty* n’a pas de fonctions virtuelles

la classe *Ty* n’a aucune base virtuelle

la classe n'a aucun membre de données non statique volatile ;

toutes les bases directes de la classe *Ty* ont des constructeurs de déplacement trivial

les classes de tous les membres de données non statiques de type de classe ont des constructeurs de déplacement triviaux ;

les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs de déplacement triviaux.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
