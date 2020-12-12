---
description: 'En savoir plus sur : erreur du compilateur C2492'
title: Erreur du compilateur C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: ef31b2136a2cfc0422832899dba14ffb3108d965
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283671"
---
# <a name="compiler-error-c2492"></a>Erreur du compilateur C2492

'*variable*' : les données avec une durée de stockage de thread ne peuvent pas avoir d’interface dll

La variable est déclarée avec l’attribut de [thread](../../cpp/thread.md) et avec l’interface dll. L’adresse de la `thread` variable n’est pas connue jusqu’au moment de l’exécution. elle ne peut donc pas être liée à une importation ou une exportation de dll.

L’exemple suivant génère l’C2492 :

```cpp
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```
