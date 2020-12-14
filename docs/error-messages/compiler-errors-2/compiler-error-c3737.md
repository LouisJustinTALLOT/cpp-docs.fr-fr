---
description: 'En savoir plus sur : erreur du compilateur C3737'
title: Erreur du compilateur C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: 0b7c604f49c710334eb9ddfafa253df90c72103c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244971"
---
# <a name="compiler-error-c3737"></a>Erreur du compilateur C3737

'Delegate' : un délégué ne peut pas avoir de convention d’appel explicite

Vous ne pouvez pas spécifier la [Convention d’appel](../../cpp/calling-conventions.md) pour un **`delegate`** .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3737 :

```cpp
// C3737a.cpp
// compile with: /clr
delegate void __stdcall MyFunc();   // C3737
// Try the following line instead.
// delegate void MyFunc();

int main() {
}
```
