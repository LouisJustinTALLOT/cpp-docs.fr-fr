---
title: Erreur du compilateur C2333
ms.date: 11/04/2016
f1_keywords:
- C2333
helpviewer_keywords:
- C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
ms.openlocfilehash: e9119a8375a276a59cbf3a6db9541f6ccaef5122
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300818"
---
# <a name="compiler-error-c2333"></a>Erreur du compilateur C2333

'fonction' : erreur dans la déclaration de fonction ; corps de la fonction ignoré

Cette erreur se produit après une autre erreur, pour les fonctions membres définies à l’intérieur de leur classe.

L’exemple suivant génère l’erreur C2333 :

```
// C2333.cpp
struct s1 {
   s1(s1) {}   // C2333
};
```