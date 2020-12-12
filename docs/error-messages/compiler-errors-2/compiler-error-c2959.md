---
description: 'En savoir plus sur : erreur du compilateur C2959'
title: Erreur du compilateur C2959
ms.date: 11/04/2016
f1_keywords:
- C2959
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
ms.openlocfilehash: aa5da1db36ce8544e95ad509402b066e664faf18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210424"
---
# <a name="compiler-error-c2959"></a>Erreur du compilateur C2959

une classe ou une fonction générique ne peut pas être membre d’un modèle

Pour plus d’informations, consultez [Windows Runtime et modèles managés](../../extensions/windows-runtime-and-managed-templates-cpp-component-extensions.md) et [génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2959.

```cpp
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```
