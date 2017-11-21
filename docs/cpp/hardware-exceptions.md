---
title: "Exceptions matérielles | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7a130e60403c9570d647955a6ad2d86f2ba49d1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="hardware-exceptions"></a>Exceptions matérielles
La plupart des exceptions standard identifiées par le système d'exploitation sont des exceptions définies par le matériel. Windows identifie quelques exceptions logicielles de bas niveau, mais celles-ci sont généralement gérées de façon optimale par le système d'exploitation.  
  
 Windows mappe les erreurs matérielles des différents processeurs aux codes d'exception figurant dans cette section. Dans certains cas, un processeur peut générer uniquement un sous-ensemble de ces exceptions. Windows prétraite les informations sur l'exception et émet le code d'exception approprié.  
  
 Les exceptions matérielles identifiées par Windows sont résumées dans le tableau suivant :  
  
|Code d'exception|Raison de l'exception|  
|--------------------|------------------------|  
|**STATUS_ACCESS_VIOLATION**|Lecture ou écriture à un emplacement mémoire inaccessible.|  
|**STATUS_BREAKPOINT**|Rencontre d'un point d'arrêt défini par le matériel ; utilisé uniquement par les débogueurs.|  
|**STATUS_DATATYPE_MISALIGNMENT**|Lecture ou écriture dans les données à une adresse qui n'est pas correctement alignée ; par exemple, des entités 16 bits doivent être alignées sur des limites de 2 octets. (Non applicable pour Intel 80*x*86 processeurs.)|  
|**STATUS_FLOAT_DIVIDE_BY_ZERO**|Division du type à virgule flottante par 0,0.|  
|**STATUS_FLOAT_OVERFLOW**|Dépassement de l'exposant positif maximal du type à virgule flottante.|  
|**STATUS_FLOAT_UNDERFLOW**|Dépassement de la grandeur de l'exposant négatif le plus bas du type à virgule flottante.|  
|**STATUS_FLOATING_RESEVERED_OPERAND**|Utilisation d'un format à virgule flottante réservé (utilisation non valide de format).|  
|**STATUS_ILLEGAL_INSTRUCTION**|Tentative d'exécution d'un code d'instruction non défini par le processeur.|  
|**STATUS_PRIVILEGED_INSTRUCTION**|Exécution d'une instruction non autorisée dans le mode actuel de l'ordinateur.|  
|**STATUS_INTEGER_DIVIDE_BY_ZERO**|Division d'un type entier par 0.|  
|**STATUS_INTEGER_OVERFLOW**|Tentative d'une opération qui dépasse la plage de l'entier.|  
|**STATUS_SINGLE_STEP**|Exécution d'une instruction en mode pas à pas ; utilisé uniquement par les débogueurs.|  
  
 Un grand nombre des exceptions répertoriées dans le tableau précédent sont destinées à être gérées par les débogueurs, le système d'exploitation ou un autre code de bas niveau. À l'exception des erreurs relatives aux entiers et aux nombres à virgule flottante, votre code ne doit pas gérer ces erreurs. Ainsi, vous devez généralement utiliser le filtre de gestion des exceptions pour ignorer les exceptions (valeur 0). Sinon, vous risquez d'empêcher les mécanismes de niveau inférieur de réagir de manière appropriée. Vous pouvez cependant prendre en charge les précautions appropriées contre les conséquences possibles de ces erreurs de bas niveau par [l’écriture de gestionnaires de terminaisons](../cpp/writing-a-termination-handler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)   
 [Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)