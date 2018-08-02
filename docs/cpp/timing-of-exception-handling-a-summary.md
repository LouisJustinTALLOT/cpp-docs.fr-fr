---
title: 'Minutage de la gestion des exceptions : un résumé | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f45b6ee85924106e949a7487f133b8e3fbe0b9e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465007"
---
# <a name="timing-of-exception-handling-a-summary"></a>Synchronisation de la gestion des exceptions : Résumé
Un gestionnaire de terminaisons est exécuté quelle que soit la façon dont le **__try** bloc d’instructions est terminé. Causes incluent hors de la **__try** bloc, un `longjmp` instruction qui transfère le contrôle hors du bloc et le déroulement de la pile en raison de la gestion des exceptions.  
  
> [!NOTE]
>  Visual C++ prend en charge deux formes des instructions `setjmp` et `longjmp`. La version rapide ignore la gestion du bloc de fin mais est plus efficace. Pour utiliser cette version, incluez le fichier \<setjmp.h >. L'autre version prend en charge la gestion du bloc de fin, comme il est décrit dans le paragraphe précédent. Pour utiliser cette version, incluez le fichier \<setjmpex.h >. L'augmentation des performances de la version rapide dépend de la configuration matérielle.  
  
 Le système d'exploitation exécute tous les gestionnaires de terminaisons dans l'ordre approprié avant que tout autre code soit exécuté, notamment le corps d'un gestionnaire d'exceptions.  
  
 Lorsque la cause de l'interruption est une exception, le système doit d'abord exécuter la partie de filtre d'un ou plusieurs gestionnaires d'exceptions avant de décider ce qui doit être terminé. L'ordre des événements est le suivant :  
  
1.  une exception est levée.  
  
2.  Le système examine la hiérarchie des gestionnaires d'exceptions actifs et applique le filtre du gestionnaire avec la priorité la plus élevée. C'est le gestionnaire d'exceptions dernièrement installé et le plus profondément imbriqué en termes de blocs et d'appels de fonction.  
  
3.  Si ce filtre passe la main (retourne 0), le processus se poursuit jusqu'à ce qu'il trouve un filtre qui ne passe pas la main.  
  
4.  Si ce filtre retourne -1, l’exécution continue où l’exception a été levée et aucun arrêt n’a lieu.  
  
5.  Si le filtre retourne 1, les événements suivants se produisent :  
  
    -   Le système déroule la pile, effaçant tous les frames de pile entre le code en cours d'exécution (où l'exception a été levée) et le frame de pile qui contient le gestionnaire d'exceptions qui prend la main.  
  
    -   Au fur et à mesure que la pile est déroulée, chaque gestionnaire de terminaisons figurant sur la pile est exécuté.  
  
    -   Le gestionnaire d'exceptions lui-même est exécuté.  
  
    -   La ligne de code prend la main après la fin de ce gestionnaire d'exceptions.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un gestionnaire de terminaisons](../cpp/writing-a-termination-handler.md)   
 [Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)