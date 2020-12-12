---
description: 'En savoir plus sur : erreur du compilateur C2504'
title: Erreur du compilateur C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 2a2269d750673a912096b497c10a9b112c23207c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213024"
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
