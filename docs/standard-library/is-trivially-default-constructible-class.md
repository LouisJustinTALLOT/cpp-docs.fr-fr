---
title: is_trivially_default_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: b35458ca280285eb699c9b12b15b705660299ef2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413409"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible, classe

Teste si le type a un constructeur par défaut trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est une classe qui a un constructeur trivial, sinon, sa valeur est false.

Un constructeur par défaut pour une classe *Ty* est trivial si :

- il s'agit d'un constructeur par défaut déclaré implicitement ;

- la classe *Ty* n’a aucune fonction virtuelle

- la classe *Ty* n’a aucune base virtuelle ;

- toutes les bases directes de la classe *Ty* ont des constructeurs triviaux

- les classes de tous les membres de données non statiques de type de classe ont des constructeurs triviaux ;

- les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs triviaux.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
