---
description: 'En savoir plus sur : erreur du compilateur C2570'
title: Erreur du compilateur C2570
ms.date: 11/04/2016
f1_keywords:
- C2570
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
ms.openlocfilehash: faebc117991262c8fff94ef75f18d6e59c884315
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209020"
---
# <a name="compiler-error-c2570"></a>Erreur du compilateur C2570

'identificateur' : une Union ne peut pas avoir de classes de base

Une Union dérive d’une classe, d’une structure ou d’une Union. Cette opération n’est pas autorisée. Déclarez le type dérivé en tant que classe ou structure à la place.

L’exemple suivant génère l’C2570 :

```cpp
// C2570.cpp
// compile with: /c
class base {};
union hasPubBase : public base {};   // C2570
union hasNoBase {};   // OK
```
