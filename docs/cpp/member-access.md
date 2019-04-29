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
ms.openlocfilehash: 34527f818b135fd5af629ebb69feaffd03b715fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301628"
---
# <a name="member-access"></a>Accès aux membres

Accès au membre de classe peut être contrôlé en surchargeant l’opérateur d’accès au membre (**->**). Cet opérateur est considéré comme un opérateur unaire dans cette utilisation, et la fonction surchargée d'opérateur doit être une fonction membre de classe. Par conséquent, la déclaration pour une telle fonction est :

## <a name="syntax"></a>Syntaxe

```
class-type *operator->()
```

## <a name="remarks"></a>Notes

où *type de classe* est le nom de la classe à laquelle appartient cet opérateur. La fonction opérateur d'accès au membre doit être une fonction membre non statique.

Cet opérateur est utilisé (souvent avec l'opérateur pointer-dereference) pour implémenter des « pointeurs intelligents » qui valident les pointeurs avant de déréférencer ou de compter l'utilisation.

L’élément de langage **.** opérateur d’accès au membre ne peut pas être surchargé.

## <a name="see-also"></a>Voir aussi

[Surcharge d'opérateur](../cpp/operator-overloading.md)