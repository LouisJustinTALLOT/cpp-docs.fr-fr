---
title: Erreur du compilateur C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 067412e59041cb98b68cb373c4671c243ab8a0ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479064"
---
# <a name="compiler-error-c3888"></a>Erreur du compilateur C3888

'name' : l’expression const associée à cette donnée membre littérale n’est pas prise en charge par C++/CLI

La donnée membre *nom* déclarée avec le mot clé [literal](../../windows/literal-cpp-component-extensions.md) est initialisée avec une valeur qui n’est pas prise en charge par le compilateur. Le compilateur prend en charge uniquement les types constant, integral, enum et string. Il est probable que l’erreur **C3888** soit causée par l’utilisation d’un tableau d’octets pour l’initialisation de la donnée membre.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez que le type de la donnée membre littérale déclarée est pris en charge.

## <a name="see-also"></a>Voir aussi

[literal](../../windows/literal-cpp-component-extensions.md)