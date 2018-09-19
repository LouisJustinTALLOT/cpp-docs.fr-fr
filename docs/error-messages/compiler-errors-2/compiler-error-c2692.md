---
title: Erreur du compilateur C2692 | Microsoft Docs
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
ms.openlocfilehash: 03a9006889c5853e77b5603484ea9d18f2474241
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088369"
---
# <a name="compiler-error-c2692"></a>Erreur du compilateur C2692

'nom_fonction' : fonctions entièrement prototypées requises dans le compilateur C avec le « / clr' option

Lors de la compilation pour .NET de code managé, le compilateur C requiert des déclarations de fonction ANSI. En outre, si une fonction ne prend aucun paramètre, il doit déclarer explicitement `void` en tant que le type de paramètre.