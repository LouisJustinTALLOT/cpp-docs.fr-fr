---
description: 'En savoir plus sur : erreur du compilateur C3062'
title: Erreur du compilateur C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: b57d03f3ef09e1d01741866d99dfff87aa5aa28d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281741"
---
# <a name="compiler-error-c3062"></a>Erreur du compilateur C3062

'enum' : l’énumérateur requiert une valeur, car le type sous-jacent est’type'

Vous pouvez spécifier un type sous-jacent pour une énumération. Toutefois, certains types vous obligent à assigner des valeurs à chaque énumérateur.

Pour plus d’informations sur les enums, consultez [enum, classe](../../extensions/enum-class-cpp-component-extensions.md).

L’exemple suivant génère l’C3062 :

```cpp
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```
