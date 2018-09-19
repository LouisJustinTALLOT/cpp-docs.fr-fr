---
title: Accès au membre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2aadccd883738fe2e6e9f57cc63f67cde6d6a6c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099938"
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