---
title: Erreur du compilateur C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: e2b08ef3e46681147c4efd77cbffadb096bbfc16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590457"
---
# <a name="compiler-error-c2492"></a>Erreur du compilateur C2492

«*variable*' : les données avec une durée de stockage de thread ne peuvent pas avoir d’interface dll

La variable est déclarée avec le [thread](../../cpp/thread.md) attribut et avec la DLL de l’interface. L’adresse de la `thread` variable n’est pas connue jusqu'à moment de l’exécution, il ne peut pas être liée à une importation de DLL ou d’exportation.

L’exemple suivant génère C2492 :

```
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```