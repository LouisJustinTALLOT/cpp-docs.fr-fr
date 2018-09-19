---
title: Erreur irrécupérable C1190 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1190
dev_langs:
- C++
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96e1ab464199466a5df13362f40ac9143be49a68
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084950"
---
# <a name="fatal-error-c1190"></a>Erreur irrécupérable C1190

le code ciblé managé requiert une option '/clr'

Vous utilisez des constructions CLR, mais vous n’avez pas spécifié **/clr**.

Pour plus d'informations, consultez [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

L’exemple suivant génère l’erreur C1190 :

```
// C1190.cpp
// compile with: /c
__gc class A {};   // C1190
ref class A {};
```