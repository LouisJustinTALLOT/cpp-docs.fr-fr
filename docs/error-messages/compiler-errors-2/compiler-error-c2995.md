---
title: L’erreur C2995 erreur de compilateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2995
dev_langs:
- C++
helpviewer_keywords:
- C2995
ms.assetid: a57cdfe0-b40b-4a67-a95c-1a49ace4842b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b63028629dd23d3bae20da0b1470cf3239c00306
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109363"
---
# <a name="compiler-error-c2995"></a>Erreur du compilateur C2995

'fonction' : modèle de fonction déjà défini

Vérifiez qu’il existe une seule définition pour chaque fonction membre d’une classe de modèle.

L’exemple suivant génère l’erreur C2995 :

```
// C2995.cpp
// compile with: /c
template <class T>
void Test(T x){}

template <class T> void Test(T x){}   // C2995
template <class T> void Test2(T x){}   // OK
```