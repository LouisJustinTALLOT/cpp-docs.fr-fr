---
description: 'En savoir plus sur : erreur du compilateur C3669'
title: Erreur du compilateur C3669
ms.date: 11/04/2016
f1_keywords:
- C3669
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
ms.openlocfilehash: b746c64af06178caf1006417f61c5f1e853cb67d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228948"
---
# <a name="compiler-error-c3669"></a>Erreur du compilateur C3669

'membre' : spécificateur de substitution’override’non autorisé sur les fonctions membres ou les constructeurs static

Une substitution a été spécifiée de manière incorrecte. Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3669.

```cpp
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```
