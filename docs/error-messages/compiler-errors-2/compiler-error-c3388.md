---
title: Erreur du compilateur C3388 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3388
dev_langs:
- C++
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4447d2d72c2a0a56df9f3a64549f201f86ddf129
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073471"
---
# <a name="compiler-error-c3388"></a>Erreur du compilateur C3388

'type' : non autorisé en tant que contrainte, 'ref class' pris par défaut pour poursuivre l’analyse

Une contrainte a été spécifiée sur un type générique, mais la contrainte n’a pas été spécifiée correctement. Consultez [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3388.

```
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```