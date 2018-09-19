---
title: Erreur du compilateur C3219 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3219
dev_langs:
- C++
helpviewer_keywords:
- C3219
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f60a17d257505752f9d2c791365f537fa02ffc2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022579"
---
# <a name="compiler-error-c3219"></a>Erreur du compilateur C3219

'param' : le paramètre générique ne peut pas être limité par plusieurs non-interfaces : 'class'

Il n’est pas correct de contraindre un paramètre générique par deux classes managées ou plus.

L’exemple suivant génère l’erreur C3219 :

```
// C3219.cpp
// compile with: /clr
ref class A {};
ref class B {};

generic <class T>
where T : A, B
ref class E {};   // C3219
```

L’exemple suivant illustre une résolution possible :

```
// C3219b.cpp
// compile with: /clr /c
ref class A {};

interface struct C {};

generic <class T>
where T : A
ref class E {};
```