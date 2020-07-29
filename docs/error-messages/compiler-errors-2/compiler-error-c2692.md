---
title: Erreur du compilateur C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: a82ee0bead9e4e7a92c16df89eee86288f562de9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216100"
---
# <a name="compiler-error-c2692"></a>Erreur du compilateur C2692

'function_name' : fonctions entièrement prototypées requises dans le compilateur C avec l’option'/CLR'

Lors de la compilation pour du code managé .NET, le compilateur C requiert des déclarations de fonction ANSI. En outre, si une fonction n’accepte aucun paramètre, elle doit explicitement déclarer **`void`** comme type de paramètre.
