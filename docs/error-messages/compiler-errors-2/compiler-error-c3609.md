---
title: Erreur du compilateur C3609 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3609
dev_langs:
- C++
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0048d1493a540bfb460d03ae514b6b191ead39d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016908"
---
# <a name="compiler-error-c3609"></a>Erreur du compilateur C3609

'membre' : une fonction sealed ou final doit être virtuelle

Le [sealed](../../windows/sealed-cpp-component-extensions.md) et [finale](../../cpp/final-specifier.md) mots clés sont uniquement autorisés sur une classe, struct ou une fonction membre marquée `virtual`.

L'exemple suivant génère l'erreur C3609 :

```
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
