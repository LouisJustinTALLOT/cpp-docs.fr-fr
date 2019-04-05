---
title: Erreur du compilateur C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: e4d52946126e7be6c6f2aef34b5eb5a93a0babad
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033639"
---
# <a name="compiler-error-c3888"></a>Erreur du compilateur C3888

'name' : l’expression const associée à cette donnée membre littérale n’est pas prise en charge par C++/CLI

La donnée membre *nom* déclarée avec le mot clé [literal](../../extensions/literal-cpp-component-extensions.md) est initialisée avec une valeur qui n’est pas prise en charge par le compilateur. Le compilateur prend en charge uniquement les types constant, integral, enum et string. Il est probable que l’erreur **C3888** soit causée par l’utilisation d’un tableau d’octets pour l’initialisation de la donnée membre.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez que le type de la donnée membre littérale déclarée est pris en charge.

## <a name="see-also"></a>Voir aussi

[littéral](../../extensions/literal-cpp-component-extensions.md)