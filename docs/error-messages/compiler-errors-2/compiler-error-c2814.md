---
description: 'En savoir plus sur : erreur du compilateur C2814'
title: Erreur du compilateur C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 3da888c70356abee8ae18990d521d5589a5c5069
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278387"
---
# <a name="compiler-error-c2814"></a>Erreur du compilateur C2814

'membre' : un type natif ne peut pas être imbriqué dans un type managé ou WinRT 'type'

## <a name="example"></a>Exemple

Un type natif ne peut pas être imbriqué dans un type CLR ou WinRT. L'exemple suivant génère l'erreur C2814 et montre comment la corriger.

```cpp
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
