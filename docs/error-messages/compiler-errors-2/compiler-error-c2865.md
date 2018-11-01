---
title: Erreur du compilateur C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: e95714f7a10c1c25562e8b12025ede486e66cff8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532732"
---
# <a name="compiler-error-c2865"></a>Erreur du compilateur C2865

'fonction' : comparaison non conforme pour handle_ou_pointeur

Vous pouvez comparer les références aux [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md) ou des types de référence uniquement pour l’égalité pour voir s’ils font référence au même objet (==) ou à différents objets gérés ( ! =).

Impossible de comparer les pour le classement car le runtime .NET peut déplacer des objets managés à tout moment, modifie le résultat du test.