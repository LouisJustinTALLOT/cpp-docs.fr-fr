---
title: Évaluation des jetons | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: baebf5c7b00dc069a1b0f97a9bc5ffb54f856980
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383051"
---
# <a name="evaluation-of-tokens"></a>Évaluation des jetons
Lorsque le compilateur interprète les jetons, il inclut autant de caractères que possible dans un jeton avant de passer au jeton suivant. En raison de ce comportement, le compilateur peut ne pas interpréter les jetons comme prévu, s'ils ne sont pas correctement séparés par des espaces blancs. Prenons l'expression suivante :  
  
```  
i+++j  
```  
  
 Dans cet exemple, le compilateur commence par créer l'opérateur le plus long possible (`++`) à partir des trois signes plus, puis traite le signe plus restant comme opérateur d'addition (`+`). Ainsi, l'expression est interprétée comme `(i++) + (j)`, et non pas comme `(i) + (++j)`. Dans ce cas et des cas similaires, utilisez des espaces blancs et des parenthèses pour éviter toute ambiguïté et garantir l'évaluation de l'expression appropriée.  
  
 **Section spécifique à Microsoft**  
  
 Le compilateur C traite un caractère CTRL+Z comme un indicateur de fin de fichier. Il ignore le texte après CTRL+Z.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Jetons C](../c-language/c-tokens.md)