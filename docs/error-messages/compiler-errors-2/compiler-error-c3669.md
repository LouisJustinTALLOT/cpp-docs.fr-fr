---
title: Erreur du compilateur C3669
ms.date: 11/04/2016
f1_keywords:
- C3669
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
ms.openlocfilehash: 3b0ad3aa7395f5f423c8c36f547d4a0e2ad792c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214899"
---
# <a name="compiler-error-c3669"></a>Erreur du compilateur C3669

'membre' : spécificateur de substitution 'override' pas autorisé sur les fonctions membres statiques ou les constructeurs

Un remplacement a été spécifié correctement. Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3669.

```
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```