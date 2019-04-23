---
title: Erreur du compilateur C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: 6f4157db4a2a1b1864446a082deddc73df2e2fe9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778707"
---
# <a name="compiler-error-c3062"></a>Erreur du compilateur C3062

'enum' : énumérateur requiert une valeur dans la mesure où le type sous-jacent est 'type'

Vous pouvez spécifier un type sous-jacent pour une énumération. Toutefois, certains types de vous obliger à assigner des valeurs à chaque énumérateur.

Pour plus d’informations sur les enums, consultez [classe enum](../../extensions/enum-class-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3062 :

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```