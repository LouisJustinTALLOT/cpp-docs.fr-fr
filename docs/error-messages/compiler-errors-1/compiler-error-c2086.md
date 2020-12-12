---
description: 'En savoir plus sur : erreur du compilateur C2086'
title: Erreur du compilateur C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: b98b4ed3896b11d8df434935c1b539f76640f24c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252075"
---
# <a name="compiler-error-c2086"></a>Erreur du compilateur C2086

'identificateur' : redéfinition

L’identificateur est défini plusieurs fois, ou une déclaration suivante diffère d’un précédent.

C2086 peut également être le résultat d’une génération incrémentielle pour un assembly C# référencé. Régénérez l’assembly C# pour résoudre cette erreur.

L’exemple suivant génère l’C2086 :

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
