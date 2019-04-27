---
title: Erreur du compilateur C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 094a794627b886abc7db5ba4d74c6fe97ff82461
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216124"
---
# <a name="compiler-error-c2086"></a>Erreur du compilateur C2086

'identificateur' : redéfinition

L’identificateur est défini plusieurs fois, ou une déclaration ultérieure diffère d’une précédente.

C2086 peut également être le résultat d’une génération incrémentielle pour un assembly c# référencé. Régénérer l’assembly c# pour résoudre cette erreur.

L’exemple suivant génère l’erreur C2086 :

```
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```