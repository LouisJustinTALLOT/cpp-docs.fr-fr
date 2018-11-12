---
title: Erreur du compilateur C3219
ms.date: 11/04/2016
f1_keywords:
- C3219
helpviewer_keywords:
- C3219
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
ms.openlocfilehash: a93e9ed1a8e00eaecc664bda02a70c81b6c81ded
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621687"
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