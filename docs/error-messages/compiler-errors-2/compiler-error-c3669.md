---
title: Erreur du compilateur C3669 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3669
dev_langs:
- C++
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7588ec3862c914fd998a7b5a3f59ff4d0bb5bbf2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088660"
---
# <a name="compiler-error-c3669"></a>Erreur du compilateur C3669

'membre' : spécificateur de substitution 'override' pas autorisé sur les fonctions membres statiques ou les constructeurs

Un remplacement a été spécifié correctement. Pour plus d’informations, consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3669.

```
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```