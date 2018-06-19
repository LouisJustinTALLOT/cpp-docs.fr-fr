---
title: La Notation C.1 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39e8610524e20aa99ea316d62f36b512700e377e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686813"
---
# <a name="c1-notation"></a>C.1 Notation
Les règles de grammaire se composent du nom d’un non terminal, suivi du signe deux-points, suivi d’autres solutions de remplacement sur des lignes distinctes.  
  
 L’expression syntaxique termopt indique que le terme est facultatif dans le remplacement.  
  
 L’expression syntaxique *terme*optseq équivaut à *terme-seq*opt avec les règles supplémentaires suivantes :  
  
 *terme-seq* :  
  
 *Terme*  
  
 *terme-seq terme*  
  
 *terme-seq* , *terme*