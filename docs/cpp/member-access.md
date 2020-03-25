---
title: Accès aux membres
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 12ea612625e21a8a13021b75e92f3752b0b5ce80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179417"
---
# <a name="member-access"></a>Accès aux membres

L’accès au membre de classe peut être contrôlé en surchargeant l’opérateur d’accès aux membres ( **->** ). Cet opérateur est considéré comme un opérateur unaire dans cette utilisation, et la fonction surchargée d'opérateur doit être une fonction membre de classe. Par conséquent, la déclaration pour une telle fonction est :

## <a name="syntax"></a>Syntaxe

```
class-type *operator->()
```

## <a name="remarks"></a>Notes

où *Class-type* est le nom de la classe à laquelle appartient cet opérateur. La fonction opérateur d'accès au membre doit être une fonction membre non statique.

Cet opérateur est utilisé (souvent avec l'opérateur pointer-dereference) pour implémenter des « pointeurs intelligents » qui valident les pointeurs avant de déréférencer ou de compter l'utilisation.

L’élément de langage **.** l’opérateur d’accès aux membres ne peut pas être surchargé.

## <a name="see-also"></a>Voir aussi

[Surcharge d'opérateur](../cpp/operator-overloading.md)
