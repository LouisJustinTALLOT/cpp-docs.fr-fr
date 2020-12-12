---
description: 'En savoir plus sur : erreur du compilateur C2588'
title: Erreur du compilateur C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: 7f723f826a5d4e609c0766c5287a0fffdee72d18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177573"
---
# <a name="compiler-error-c2588"></a>Erreur du compilateur C2588

' :: ~ identificateur' : destructeur global non conforme

Le destructeur est défini pour autre chose qu’une classe, une structure ou une Union. Cette opération n’est pas autorisée.

Cette erreur peut être due à un nom de classe, de structure ou d’Union manquant sur le côté gauche de l’opérateur de résolution de portée ( `::` ).

L’exemple suivant génère l’C2588 :

```cpp
// C2588.cpp
~F();   // C2588
```
