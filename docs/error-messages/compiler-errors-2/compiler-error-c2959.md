---
title: Erreur du compilateur C2959 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2959
dev_langs:
- C++
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f225dccc917e34fba690064d66cf1cda36219877
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078970"
---
# <a name="compiler-error-c2959"></a>Erreur du compilateur C2959

une classe ou fonction générique ne peut pas être un membre d’un modèle

Pour plus d’informations, consultez [Windows Runtime et modèles gérés](../../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md) et [génériques](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C2959.

```
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```