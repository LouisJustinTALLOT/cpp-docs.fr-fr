---
title: Erreur du compilateur C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 417763e8c26918d3cd83702b283244d1c13d9d1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735747"
---
# <a name="compiler-error-c2086"></a>Erreur du compilateur C2086

'identificateur' : redéfinition

L’identificateur est défini plusieurs fois, ou une déclaration suivante diffère d’un précédent.

C2086 peut également être le résultat d’une génération incrémentielle pour un C# assembly référencé. Régénérez l' C# assembly pour résoudre cette erreur.

L’exemple suivant génère l’C2086 :

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
