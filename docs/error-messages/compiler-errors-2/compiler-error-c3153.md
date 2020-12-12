---
description: 'En savoir plus sur : erreur du compilateur C3153'
title: Erreur du compilateur C3153
ms.date: 11/04/2016
f1_keywords:
- C3153
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
ms.openlocfilehash: 93b028e08963a8d124defe660966a75595c57771
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322044"
---
# <a name="compiler-error-c3153"></a>Erreur du compilateur C3153

'interface' : vous ne pouvez pas créer une instance d’une interface

Une interface ne peut pas être instanciée. Pour utiliser les membres d’une interface, dérivez une classe de l’interface, implémentez les membres d’interface, puis utilisez les membres.

L’exemple suivant génère l’C3153 :

```cpp
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```
