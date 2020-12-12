---
description: 'En savoir plus sur : erreur du compilateur C3194'
title: Erreur du compilateur C3194
ms.date: 11/04/2016
f1_keywords:
- C3194
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
ms.openlocfilehash: 7513b9d4964b6eb0024c3b51480f188243bf2637
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174037"
---
# <a name="compiler-error-c3194"></a>Erreur du compilateur C3194

'membre' : un type valeur ne peut pas avoir d’opérateur d’assignation

Les fonctions membres spéciales qui requièrent l’appel automatique par le compilateur, comme un constructeur de copie ou un opérateur d’assignation de copie, ne sont pas prises en charge dans une classe value.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3194.

```cpp
// C3194.cpp
// compile with: /clr /c
value struct MyStruct {
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194
};

ref struct MyStruct2 {
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK
};
```
