---
title: Erreur irrécupérable C1026 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db9167383df48dad274ef8941defaa53f51d3bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068986"
---
# <a name="fatal-error-c1026"></a>Erreur irrécupérable C1026

dépassement de capacité de la pile de l'analyseur, programme trop complexe

L’espace requis pour analyser le programme a provoqué un dépassement de capacité de pile du compilateur.

Réduire la complexité des expressions en :

- Diminution de l’imbrication dans `for` et `switch` instructions. Placer des instructions plus profondément imbriquées dans des fonctions séparées.

- Découper des expressions longues qui impliquent des opérateurs de virgules ou des appels de fonction.