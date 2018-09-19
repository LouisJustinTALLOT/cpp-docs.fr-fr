---
title: Erreur du compilateur C2032 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ab02ca695ec94f25054e3490232b782a46a53a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064007"
---
# <a name="compiler-error-c2032"></a>Erreur du compilateur C2032

'identificateur' : fonction ne peut pas être membre de struct/union 'StructOuUnion'

La structure ou union a une fonction membre, ce qui est autorisée en C++, mais pas dans C. Pour résoudre l’erreur, compilez comme un programme C++ ou supprimez la fonction membre.

L’exemple suivant génère l’erreur C2032 :

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

Solution possible :

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```