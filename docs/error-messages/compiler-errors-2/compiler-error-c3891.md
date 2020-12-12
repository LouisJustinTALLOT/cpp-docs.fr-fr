---
description: 'En savoir plus sur : erreur du compilateur C3891'
title: Erreur du compilateur C3891
ms.date: 11/04/2016
f1_keywords:
- C3891
helpviewer_keywords:
- C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
ms.openlocfilehash: df853f3ed0a163b48e75d54561d00298edd215b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144298"
---
# <a name="compiler-error-c3891"></a>Erreur du compilateur C3891

'var' : un membre de données littéral ne peut pas être utilisé comme l-value

Une variable [littérale](../../extensions/literal-cpp-component-extensions.md) est const, et sa valeur ne peut pas être modifiée une fois qu’elle a été initialisée dans la déclaration.

L’exemple suivant génère l’C3891 :

```cpp
// C3891.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3891
}
```
