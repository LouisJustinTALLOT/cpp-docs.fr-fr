---
title: Erreur du compilateur C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 7ce57cd50e9ec83cf80ec64e14f49eb9714f9208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177090"
---
# <a name="compiler-error-c2692"></a>Erreur du compilateur C2692

'function_name' : fonctions entièrement prototypées requises dans le compilateur C avec l’option'/CLR'

Lors de la compilation pour du code managé .NET, le compilateur C requiert des déclarations de fonction ANSI. En outre, si une fonction n’accepte aucun paramètre, elle doit déclarer explicitement `void` comme type de paramètre.
