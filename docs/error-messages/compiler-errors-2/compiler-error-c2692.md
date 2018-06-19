---
title: Erreur du compilateur C2692 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a02110750a748b5c520df7d202a87957f227a802
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230986"
---
# <a name="compiler-error-c2692"></a>Erreur du compilateur C2692
'nom_fonction' : fonctions entièrement prototypées requises dans le compilateur C avec le ' / clr' option  
  
 Lors de la compilation pour .NET de code managé, le compilateur C requiert des déclarations de fonction ANSI. En outre, si une fonction n’accepte aucun paramètre, il doit déclarer explicitement `void` en tant que le type de paramètre.