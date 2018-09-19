---
title: Erreur du compilateur C3198 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3198
dev_langs:
- C++
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb91d6f7b3ef6b8204a5f8bfb753db98ab6f93d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023382"
---
# <a name="compiler-error-c3198"></a>Erreur du compilateur C3198

utilisation non valide des pragmas à virgule flottante : le pragma fenv_access ne fonctionne qu’en mode précision

[fenv_access](../../preprocessor/fenv-access.md) pragma a été utilisé sous un [/FP](../../build/reference/fp-specify-floating-point-behavior.md) paramètre autre que **/fp : precise**.

L’exemple suivant génère l’erreur C3198 :

```
// C3198.cpp
// compile with: /fp:fast
#pragma fenv_access(on)   // C3198
```