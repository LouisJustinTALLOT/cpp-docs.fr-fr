---
title: Du compilateur (niveau 1) d’avertissement C4041 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff2c8066557e420ecd7de561d7731b7be733315
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085782"
---
# <a name="compiler-warning-level-1-c4041"></a>Avertissement du compilateur (niveau 1) C4041

limite du compilateur : arrêt de la sortie de l’explorateur

Les informations du navigateur dépassent la limite du compilateur.

Cet avertissement peut être dû à une compilation avec [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informations du navigateur comprenant des variables locales).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Compilez avec /Fr (informations du navigateur sans variables locales).

1. Désactivez la sortie de navigateur (compilez sans /FR ou /Fr).