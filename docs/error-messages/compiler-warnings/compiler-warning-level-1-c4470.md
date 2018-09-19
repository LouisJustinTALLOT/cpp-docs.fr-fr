---
title: Compilateur avertissement (niveau 1) C4470 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4470
dev_langs:
- C++
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a660192b11e98bc34871e1f845c872fe27fb9ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076981"
---
# <a name="compiler-warning-level-1-c4470"></a>Avertissement du compilateur (niveau 1) C4470

pragmas de contrôle à virgule flottante ignorés sous /clr

Les pragmas de contrôle à virgule flottante :

- [fenv_access](../../preprocessor/fenv-access.md)

- [float_control](../../preprocessor/float-control.md)

- [fp_contract](../../preprocessor/fp-contract.md)

n’ont aucun effet sous [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

L’exemple suivant génère l’erreur C4470 :

```
// C4470.cpp
// compile with: /clr /W1 /LD
#pragma float_control(except, on)   // C4470
```