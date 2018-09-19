---
title: Erreur du compilateur C2585 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec7b1e9c1e5e7894740cc80f9c030fa1ee26ec0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028842"
---
# <a name="compiler-error-c2585"></a>Erreur du compilateur C2585

une conversion explicite en 'type' est AMBIGUE

La conversion de type peut produire plusieurs résultats.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Conversion d’un type de classe ou structure basé sur l’héritage multiple. Si le type hérite de la classe de base même plusieurs fois, la fonction de conversion ou un opérateur doit utiliser la résolution de portée (`::`) de spécifier les classes héritées à utiliser dans la conversion.

1. Un opérateur de conversion et un constructeur définis effectue la même conversion.