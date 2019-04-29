---
title: Erreur du compilateur C2449
ms.date: 11/04/2016
f1_keywords:
- C2449
helpviewer_keywords:
- C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
ms.openlocfilehash: f674bbec7cee8c00792848ee7e51b1e46299dd58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302070"
---
# <a name="compiler-error-c2449"></a>Erreur du compilateur C2449

trouvé ' {' à la portée du fichier (en-tête de fonction manquant ?)

Une accolade ouvrante se produit au niveau de la portée du fichier.

Cette erreur peut être provoquée par un point-virgule entre un en-tête de fonction et l’accolade ouvrante de la définition de fonction.

L’exemple suivant génère l’erreur C2499 :

```
// C2449.c
// compile with: /c
void __stdcall func(void) {}   // OK
void __stdcall func(void);  // extra semicolon on this line
{                         // C2449 detected here
```