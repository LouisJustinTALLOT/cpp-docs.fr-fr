---
title: Exceptions matérielles
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 59b74f47cd86d94b50ab9213b3e517c2b08db696
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246549"
---
# <a name="hardware-exceptions"></a>Exceptions matérielles

La plupart des exceptions standard identifiées par le système d'exploitation sont des exceptions définies par le matériel. Windows identifie quelques exceptions logicielles de bas niveau, mais celles-ci sont généralement gérées de façon optimale par le système d'exploitation.

Windows mappe les erreurs matérielles des différents processeurs aux codes d'exception figurant dans cette section. Dans certains cas, un processeur peut générer uniquement un sous-ensemble de ces exceptions. Windows prétraite les informations sur l'exception et émet le code d'exception approprié.

Les exceptions matérielles identifiées par Windows sont résumées dans le tableau suivant :

|Code d'exception|Raison de l'exception|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|Lecture ou écriture à un emplacement mémoire inaccessible.|
|STATUS_BREAKPOINT|Rencontre d'un point d'arrêt défini par le matériel ; utilisé uniquement par les débogueurs.|
|STATUS_DATATYPE_MISALIGNMENT|Lecture ou écriture dans les données à une adresse qui n'est pas correctement alignée ; par exemple, des entités 16 bits doivent être alignées sur des limites de 2 octets. (Not applicable to Intel 80*x*86 processors.)|
|STATUS_FLOAT_DIVIDE_BY_ZERO|Division du type à virgule flottante par 0,0.|
|STATUS_FLOAT_OVERFLOW|Dépassement de l'exposant positif maximal du type à virgule flottante.|
|STATUS_FLOAT_UNDERFLOW|Dépassement de la grandeur de l'exposant négatif le plus bas du type à virgule flottante.|
|STATUS_FLOATING_RESEVERED_OPERAND|Utilisation d'un format à virgule flottante réservé (utilisation non valide de format).|
|STATUS_ILLEGAL_INSTRUCTION|Tentative d'exécution d'un code d'instruction non défini par le processeur.|
|STATUS_PRIVILEGED_INSTRUCTION|Exécution d'une instruction non autorisée dans le mode actuel de l'ordinateur.|
|STATUS_INTEGER_DIVIDE_BY_ZERO|Division d'un type entier par 0.|
|STATUS_INTEGER_OVERFLOW|Tentative d'une opération qui dépasse la plage de l'entier.|
|STATUS_SINGLE_STEP|Exécution d'une instruction en mode pas à pas ; utilisé uniquement par les débogueurs.|

Un grand nombre des exceptions répertoriées dans le tableau précédent sont destinées à être gérées par les débogueurs, le système d'exploitation ou un autre code de bas niveau. À l'exception des erreurs relatives aux entiers et aux nombres à virgule flottante, votre code ne doit pas gérer ces erreurs. Ainsi, vous devez généralement utiliser le filtre de gestion des exceptions pour ignorer les exceptions (valeur 0). Sinon, vous risquez d'empêcher les mécanismes de niveau inférieur de réagir de manière appropriée. You can, however, take appropriate precautions against the potential effect of these low-level errors by [writing termination handlers](../cpp/writing-a-termination-handler.md).

## <a name="see-also"></a>Voir aussi

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)