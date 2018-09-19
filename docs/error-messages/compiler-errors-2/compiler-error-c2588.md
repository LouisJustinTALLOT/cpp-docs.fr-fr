---
title: Erreur du compilateur C2588 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d656dbde06d6052fd10611675f2cff8818cdb6e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108569"
---
# <a name="compiler-error-c2588"></a>Erreur du compilateur C2588

' :: ~ identificateur ' : destructeur global non conforme

Le destructeur est défini pour un élément autre qu’une classe, une structure ou une union. Cette opération n’est pas autorisée.

Cette erreur peut être due à un manquant nom de classe, structure ou union sur le côté gauche de la résolution de portée (`::`) opérateur.

L’exemple suivant génère l’erreur C2588 :

```
// C2588.cpp
~F();   // C2588
```