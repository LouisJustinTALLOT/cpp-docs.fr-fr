---
title: Dépassement négatif de valeurs à virgule flottante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ceaa41dcaca88c7857a03c16ccccabdba086fd0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387822"
---
# <a name="underflow-of-floating-point-values"></a>Dépassement des valeurs à virgule flottante
**ANSI 4.5.1** Indique si les fonctions mathématiques définissent l'expression d'entier `errno` sur la valeur de la macro `ERANGE` sur les erreurs de plage de dépassement de capacité négatif  
  
 Un dépassement de capacité négatif à virgule flottante ne définit pas l'expression `errno` sur `ERANGE`. Lorsqu'une valeur s'approche de zéro et effectue finalement un dépassement de capacité négatif, la valeur est définie sur zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions des bibliothèques](../c-language/library-functions.md)