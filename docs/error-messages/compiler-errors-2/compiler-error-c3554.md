---
title: Erreur du compilateur C3554 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3554
dev_langs:
- C++
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b1760607a335d4dd56ec711eef76f5a68550d64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089500"
---
# <a name="compiler-error-c3554"></a>Erreur du compilateur C3554

impossible d'associer 'decltype' à un autre spécificateur de type

Vous ne pouvez pas qualifier le mot clé `decltype()` avec n’importe quel spécificateur de type. Par exemple, le fragment de code suivant génère l’erreur C3554.

```
int x;
unsigned decltype(x); // C3554
```