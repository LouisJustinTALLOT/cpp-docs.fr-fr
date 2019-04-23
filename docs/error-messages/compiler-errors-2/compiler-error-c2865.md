---
title: Erreur du compilateur C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: 38b7dd86a57c3cd89811c6489e51fb4271fd7b79
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777141"
---
# <a name="compiler-error-c2865"></a>Erreur du compilateur C2865

'fonction' : comparaison non conforme pour handle_ou_pointeur

Vous pouvez comparer les références aux [les Classes et Structs](../../extensions/classes-and-structs-cpp-component-extensions.md) ou des types de référence uniquement pour l’égalité pour voir s’ils font référence au même objet (==) ou à différents objets gérés ( ! =).

Impossible de comparer les pour le classement car le runtime .NET peut déplacer des objets managés à tout moment, modifie le résultat du test.