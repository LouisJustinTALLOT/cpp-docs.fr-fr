---
title: Erreur du compilateur C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: c469f4944417c9116c7316b01642dd4b370b8c4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611157"
---
# <a name="compiler-error-c2692"></a>Erreur du compilateur C2692

'nom_fonction' : fonctions entièrement prototypées requises dans le compilateur C avec le « / clr' option

Lors de la compilation pour .NET de code managé, le compilateur C requiert des déclarations de fonction ANSI. En outre, si une fonction ne prend aucun paramètre, il doit déclarer explicitement `void` en tant que le type de paramètre.