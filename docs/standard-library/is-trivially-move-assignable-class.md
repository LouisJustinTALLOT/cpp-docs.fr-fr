---
title: is_trivially_move_assignable, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1248c8efd06069863a9f78a94378fe7aed651011
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856083"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable, classe

Teste si le type a un opérateur d'assignation de déplacement trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Paramètres

`Ty` Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type `Ty` est une classe qui a un opérateur d'assignation de déplacement trivial. Sinon, sa valeur est false.

Un opérateur d'assignation de déplacement pour une classe `Ty` est trivial si :

il est fourni implicitement ;

la classe `Ty` n'a aucune fonction virtuelle ;

la classe `Ty` n'a aucune base virtuelle ;

les classes de tous les membres de données non statiques de type classe possèdent des opérateurs d'assignation de déplacement triviaux ;

les classes de tous les membres de données non statiques de type tableau de classe possèdent des opérateurs d'assignation de déplacement triviaux.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
