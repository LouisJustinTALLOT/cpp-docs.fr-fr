---
description: 'En savoir plus sur : erreur du compilateur C2054'
title: Erreur du compilateur C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: b86c805a5687679cfa4bb5ed667c3bcf3adbad94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341358"
---
# <a name="compiler-error-c2054"></a>Erreur du compilateur C2054

' ('doit suivre’identifier'

L’identificateur de fonction est utilisé dans un contexte qui requiert des parenthèses de fin.

Cette erreur peut être due à l’omission d’un signe égal (=) sur une initialisation complexe.

L’exemple suivant génère l’C2054 :

```c
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

Solution possible :

```c
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```
