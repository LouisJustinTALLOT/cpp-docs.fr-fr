---
title: Erreur du compilateur C2865 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc0a49f8e6ab42f7e607cd5f4f7cc91f6895abe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035161"
---
# <a name="compiler-error-c2865"></a>Erreur du compilateur C2865

'fonction' : comparaison non conforme pour handle_ou_pointeur

Vous pouvez comparer les références aux [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md) ou des types de référence uniquement pour l’égalité pour voir s’ils font référence au même objet (==) ou à différents objets gérés ( ! =).

Impossible de comparer les pour le classement car le runtime .NET peut déplacer des objets managés à tout moment, modifie le résultat du test.