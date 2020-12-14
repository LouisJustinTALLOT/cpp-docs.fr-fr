---
description: 'En savoir plus sur : erreur du compilateur C2865'
title: Erreur du compilateur C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: 0c57fdb120eb147b3877cc834e142ab92f147aaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220745"
---
# <a name="compiler-error-c2865"></a>Erreur du compilateur C2865

'fonction' : comparaison non conforme pour handle_or_pointer

Vous pouvez comparer des références à des [classes et des structs](../../extensions/classes-and-structs-cpp-component-extensions.md) ou des types de référence managés uniquement pour déterminer s’ils font référence au même objet (= =) ou à des objets différents ( ! =).

Vous ne pouvez pas les comparer pour le classement, car le Runtime .NET peut déplacer des objets managés à tout moment, en modifiant le résultat du test.
