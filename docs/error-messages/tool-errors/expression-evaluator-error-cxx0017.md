---
title: Évaluateur d’expression, erreur CXX0017 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 431071137fb3f5b1b276327ee7d21f323ac24c5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136235"
---
# <a name="expression-evaluator-error-cxx0017"></a>Évaluateur d'expression, erreur CXX0017

symbole introuvable

Impossible de trouver un symbole spécifié dans une expression.

Une des causes possibles de cette erreur est une incompatibilité de cas dans le nom du symbole. Étant donné que C et C++ sont des langages de respect de la casse, un nom de symbole doit figurer dans la casse exacte dans laquelle il est défini dans la source.

Cette erreur peut se produire lorsque vous tentez de convertir une variable afin des pour regarder la variable pendant le débogage. Le `typedef` déclare un nouveau nom pour un type, mais il ne définit pas un nouveau type. La conversion de type tentée dans le débogueur requiert le nom d’un type défini.

Cette erreur est identique à CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Assurez-vous que le symbole est déjà déclaré au niveau du point du programme où il est utilisé.

1. Pour effectuer un cast de variables dans le débogueur, utilisez un nom de type réel plutôt qu’un `typedef`-nom défini.