---
title: Erreur du compilateur C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 0860f4b860b370f96c2c29046b090d5b205c63ba
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509385"
---
# <a name="compiler-error-c2504"></a>Erreur du compilateur C2504

'classe' : classe de base non définie

La classe de base est déclarée, mais jamais définie.  Causes possibles :

1. Fichier include manquant.

1. Classe de base externe non déclarée avec [extern](../../cpp/extern-cpp.md).

L’exemple suivant génère l’C2504 :

```cpp
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

Bien

```
class C{};
class D : public C {};
```
