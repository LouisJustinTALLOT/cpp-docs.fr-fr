---
description: 'En savoir plus sur : erreur du compilateur C2674'
title: Erreur du compilateur C2674
ms.date: 11/04/2016
f1_keywords:
- C2674
helpviewer_keywords:
- C2674
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
ms.openlocfilehash: c88a32eaeeda28b8ffb8daa0411a71fd773ffa2b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282040"
---
# <a name="compiler-error-c2674"></a>Erreur du compilateur C2674

une déclaration générique n’est pas autorisée dans ce contexte

Un générique a été déclaré de manière incorrecte. Pour plus d’informations, consultez [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2674.

```cpp
// C2674.cpp
// compile with: /clr /c
void F(generic <class T> ref class R1);   // C2674
generic <class T> ref class R2 {};   // OK
```
