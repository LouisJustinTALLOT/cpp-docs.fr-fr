---
description: 'En savoir plus sur : erreur du compilateur C2692'
title: Erreur du compilateur C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 5a9666bf437d65c54d0cb8c460054b2b3ebd0b55
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326682"
---
# <a name="compiler-error-c2692"></a>Erreur du compilateur C2692

'function_name' : fonctions entièrement prototypées requises dans le compilateur C avec l’option'/CLR'

Lors de la compilation pour du code managé .NET, le compilateur C requiert des déclarations de fonction ANSI. En outre, si une fonction n’accepte aucun paramètre, elle doit explicitement déclarer **`void`** comme type de paramètre.
