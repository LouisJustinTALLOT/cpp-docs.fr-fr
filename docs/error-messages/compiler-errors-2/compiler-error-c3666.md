---
title: Erreur du compilateur C3666 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3666
dev_langs:
- C++
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8637caadbe439b2da3b64593655ddd75177f353b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084079"
---
# <a name="compiler-error-c3666"></a>Erreur du compilateur C3666

'constructeur' : spécificateur 'mot_clé' non autorisé sur un constructeur de substitution

Un spécificateur de substitution a été utilisé sur un constructeur, et qui n’est pas autorisé. Pour plus d’informations, consultez [des spécificateurs de substitution](../../windows/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3666.

```
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```