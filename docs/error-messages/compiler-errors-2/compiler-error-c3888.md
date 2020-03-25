---
title: Erreur du compilateur C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 40156dfaad5965d30a32d3aa2ac574a5f91999ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176402"
---
# <a name="compiler-error-c3888"></a>Erreur du compilateur C3888

'name' : l’expression const associée à cette donnée membre littérale n’est pas prise en charge par C++/CLI

La donnée membre *nom* déclarée avec le mot clé [literal](../../extensions/literal-cpp-component-extensions.md) est initialisée avec une valeur qui n’est pas prise en charge par le compilateur. Le compilateur prend en charge uniquement les types constant, integral, enum et string. Il est probable que l’erreur **C3888** soit causée par l’utilisation d’un tableau d’octets pour l’initialisation de la donnée membre.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez que le type de la donnée membre littérale déclarée est pris en charge.

## <a name="see-also"></a>Voir aussi

[literal](../../extensions/literal-cpp-component-extensions.md)
