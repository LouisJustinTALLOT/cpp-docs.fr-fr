---
description: 'En savoir plus sur : erreur du compilateur C3880'
title: Erreur du compilateur C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: c2d279cd50716f647fbbdf51f9f9c39863d4e2d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274591"
---
# <a name="compiler-error-c3880"></a>Erreur du compilateur C3880

'var' : ne peut pas être un membre de données littéral

Le type d’un attribut [littéral](../../extensions/literal-cpp-component-extensions.md) doit être convertible en, ou au moment de la compilation, l’un des types suivants :

- type intégral

- string

- enum avec un type intégral ou sous-jacent

L’exemple suivant génère l’C3880 :

```cpp
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```
