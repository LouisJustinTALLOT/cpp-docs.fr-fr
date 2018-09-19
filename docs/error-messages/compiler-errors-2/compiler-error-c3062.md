---
title: Erreur du compilateur C3062 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95f2e58cada0b1b825fb0f065b461db6350de9fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067166"
---
# <a name="compiler-error-c3062"></a>Erreur du compilateur C3062

'enum' : énumérateur requiert une valeur dans la mesure où le type sous-jacent est 'type'

Vous pouvez spécifier un type sous-jacent pour une énumération. Toutefois, certains types de vous obliger à assigner des valeurs à chaque énumérateur.

Pour plus d’informations sur les enums, consultez [classe enum](../../windows/enum-class-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3062 :

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```