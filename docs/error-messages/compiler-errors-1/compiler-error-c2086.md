---
title: Erreur du compilateur C2086 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2086
dev_langs:
- C++
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0e0d8b105d58b0585bc31b8d340d3d7ba5fb29e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029843"
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