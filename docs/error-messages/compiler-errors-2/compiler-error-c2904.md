---
title: Erreur du compilateur C2904 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2904
dev_langs:
- C++
helpviewer_keywords:
- C2904
ms.assetid: d5802f2e-d3fc-473d-aa04-36957b4eaca5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76f305ccab68a5b0d59cb3d4246b51fed61c6bf7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061563"
---
# <a name="compiler-error-c2904"></a>Erreur du compilateur C2904

'identificateur' : nom déjà utilisé pour un modèle dans la portée actuelle

Vérifiez si le code contient des noms dupliqués.

L’exemple suivant génère l’erreur C2904 :

```
// C2904.cpp
// compile with: /c
void X();  // X is declared as a function
template<class T> class X{};  // C2904
```