---
title: Erreur du compilateur C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 8f428699aa14cbd1f021a57ed8dcabefa8b24c16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165084"
---
# <a name="compiler-error-c2504"></a>Erreur du compilateur C2504

'classe' : classe non définie de base

La classe de base est déclarée mais jamais définie.  Causes possibles :

1. Fichier include manquant.

1. Classe de base externe non déclarée avec [extern](../../cpp/using-extern-to-specify-linkage.md).

L’exemple suivant génère l’erreur C2504 :

```
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

// OK

```
class C{};
class D : public C {};
```