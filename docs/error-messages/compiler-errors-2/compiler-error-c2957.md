---
title: Erreur du compilateur C2957 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2957
dev_langs:
- C++
helpviewer_keywords:
- C2957
ms.assetid: 9cb4526f-4af8-47e9-b786-56192627ca72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38379078909799784f0cfbfd507b2f1acd4b8b93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081011"
---
# <a name="compiler-error-c2957"></a>Erreur du compilateur C2957

'delim' : délimiteur gauche non valide : '<' attendu

Une classe générique était incorrecte.

L’exemple suivant génère l’erreur C2957 :

```
// C2957.cpp
// compile with: /clr /LD
generic << class T>   // C2957
// try the following line instead
// generic < class T>
gc class C {};
```