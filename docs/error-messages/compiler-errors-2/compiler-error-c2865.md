---
title: Erreur du compilateur C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: dd4374c1a577c4c39c5dec107ed5025d7cdc79c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201694"
---
# <a name="compiler-error-c2865"></a>Erreur du compilateur C2865

'fonction' : comparaison non conforme pour handle_or_pointer

Vous pouvez comparer des références à des [classes et des structs](../../extensions/classes-and-structs-cpp-component-extensions.md) ou des types de référence managés uniquement pour déterminer s’ils font référence au même objet (= =) ou à des objets différents ( ! =).

Vous ne pouvez pas les comparer pour le classement, car le Runtime .NET peut déplacer des objets managés à tout moment, en modifiant le résultat du test.
