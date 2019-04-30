---
title: is_trivially_move_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: a1aef356716fac903b4e44a358602c709572e8ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413388"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible, classe

Teste si le type a un constructeur de déplacement trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est une classe qui a un constructeur de déplacement triviaux, sinon, sa valeur est false.

Un constructeur de déplacement pour une classe *Ty* est trivial si :

il est déclaré implicitement ;

ses types de paramètres sont équivalents à ceux d'une déclaration implicite ;

la classe *Ty* n’a aucune fonction virtuelle

la classe *Ty* n’a aucune base virtuelle ;

la classe n'a aucun membre de données non statique volatile ;

toutes les bases directes de la classe *Ty* possèdent des constructeurs de déplacement triviaux.

les classes de tous les membres de données non statiques de type de classe ont des constructeurs de déplacement triviaux ;

les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs de déplacement triviaux.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
