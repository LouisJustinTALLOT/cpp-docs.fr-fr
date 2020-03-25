---
title: Évaluateur d'expression, erreur CXX0052
ms.date: 11/04/2016
f1_keywords:
- CXX0052
helpviewer_keywords:
- CXX0052
- CAN0052
ms.assetid: 5060d479-d0a4-4682-b858-c8b9a4f324e6
ms.openlocfilehash: 5b9596313a80cb555f7daf4b65eda54a1d23a1ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184799"
---
# <a name="expression-evaluator-error-cxx0052"></a>Évaluateur d'expression, erreur CXX0052

fonction membre absente

Une fonction membre a été spécifiée en tant que point d’arrêt mais n’a pas pu être trouvée. La définition d’un point d’arrêt au niveau d’une fonction inline peut provoquer cette erreur.

Recompilez le fichier avec l’incorporation forcée (/Ob0) pour définir un point d’arrêt dans cette fonction.

Une expression a appelé une fonction qui n’a pas été définie.

Cette erreur est identique à CAN0052.
