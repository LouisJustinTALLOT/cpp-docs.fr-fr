---
description: 'En savoir plus sur : erreur du compilateur C3282'
title: Erreur du compilateur C3282
ms.date: 11/04/2016
f1_keywords:
- C3282
helpviewer_keywords:
- C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
ms.openlocfilehash: 9455f7e109da0efa87b215f0695eeeb41648c2b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311888"
---
# <a name="compiler-error-c3282"></a>Erreur du compilateur C3282

les listes de paramètres génériques ne peuvent apparaître que sur des fonctions managées ou WinRTclasses, des structs ou des fonctions

Une liste de paramètres génériques a été utilisée de façon incorrecte.  Pour plus d’informations, consultez [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3282 et montre comment la corriger.

```cpp
// C3282.cpp
// compile with: /clr /c
generic <typename T> int x;   // C3282

ref struct GC0 {
   generic <typename T> int x;   // C3282
};

// OK
generic <typename T>
ref class M {};
```
