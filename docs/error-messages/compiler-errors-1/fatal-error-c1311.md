---
title: Erreur irrécupérable C1311 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d93aa28d0cef3c07fd469349d485c4009fa4771d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091060"
---
# <a name="fatal-error-c1311"></a>Erreur irrécupérable 1311

Le format COFF ne peut pas initialiser de manière statique 'var' avec numéro octet (s) d’une adresse

Une adresse dont la valeur n’est pas connue au moment de la compilation ne peut pas être affectée de manière statique à une variable dont le type possède un stockage moins de quatre octets.

Cette erreur peut se produire sur du code qui est sinon C++ valide.

L’exemple suivant montre une condition qui peut générer l’erreur C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```