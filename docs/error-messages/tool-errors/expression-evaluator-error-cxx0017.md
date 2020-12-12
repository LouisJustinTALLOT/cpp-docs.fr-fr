---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0017'
title: Évaluateur d'expression, erreur CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: 0abb99422383f95e13d4137a5ad899730d485f87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228272"
---
# <a name="expression-evaluator-error-cxx0017"></a>Évaluateur d'expression, erreur CXX0017

symbole introuvable

Impossible de trouver un symbole spécifié dans une expression.

L’une des causes possibles de cette erreur est une incompatibilité de casse dans le nom du symbole. Comme C et C++ sont des langages qui respectent la casse, un nom de symbole doit être indiqué dans le cas exact dans lequel il est défini dans la source.

Cette erreur peut se produire lors d’une tentative de conversion d’une variable afin de surveiller la variable pendant le débogage. `typedef`Déclare un nouveau nom pour un type, mais ne définit pas de nouveau type. La conversion de type tentée dans le débogueur requiert le nom d’un type défini.

Cette erreur est identique à CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Assurez-vous que le symbole est déjà déclaré au point du programme dans lequel il est utilisé.

1. Utilisez un nom de type réel pour effectuer un cast des variables dans le débogueur, plutôt qu’un `typedef` nom défini par l’élément.
