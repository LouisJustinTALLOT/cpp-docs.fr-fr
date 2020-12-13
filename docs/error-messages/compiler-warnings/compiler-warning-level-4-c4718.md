---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4718'
title: Avertissement du compilateur (niveau 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: 9c0a24bbec0ae0cf902d905cc2dcecc492efc44b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330550"
---
# <a name="compiler-warning-level-4-c4718"></a>Avertissement du compilateur (niveau 4) C4718

'function call' : un appel récurrent n’a pas d’effets secondaires, suppression

Une fonction contient un appel récurrent, mais n’a pas d’effets secondaires. Un appel à cette fonction est en cours de suppression. L’exactitude du programme n’est pas affectée ; par contre, son comportement l’est. Si le fait de laisser l’appel peut provoquer une exception de dépassement de capacité de la pile d’exécution, la suppression de l’appel élimine ce risque.
