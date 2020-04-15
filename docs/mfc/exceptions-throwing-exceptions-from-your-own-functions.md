---
title: "Exceptions : levée d'exceptions à partir de vos propres fonctions"
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 6484594df7636fd52ac46ab1cc212c8e2ec0278e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359279"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Exceptions : levée d'exceptions à partir de vos propres fonctions

Il est possible d’utiliser le paradigme de gestion des exceptions MFC uniquement pour attraper les exceptions jetées par les fonctions dans MFC ou d’autres bibliothèques. En plus d’attraper les exceptions jetées par le code de la bibliothèque, vous pouvez jeter des exceptions à partir de votre propre code si vous écrivez des fonctions qui peuvent rencontrer des conditions exceptionnelles.

Lorsqu’une exception est lancée, l’exécution de la fonction actuelle est arrêtée et saute directement au bloc de **capture** du cadre d’exception le plus intime. Le mécanisme d’exception contourne le chemin de sortie normal d’une fonction. Par conséquent, vous devez être sûr de supprimer les blocs de mémoire qui seraient supprimés dans une sortie normale.

#### <a name="to-throw-an-exception"></a>Pour jeter une exception

1. Utilisez l’une des fonctions d’aide MFC, telles que `AfxThrowMemoryException`. Ces fonctions jettent un objet d’exception préaffecté du type approprié.

   Dans l’exemple suivant, une fonction tente d’allouer deux blocs de mémoire et jette une exception si l’une ou l’autre allocation échoue :

   [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Si la première allocation échoue, vous pouvez simplement jeter l’exception de mémoire. Si la première allocation est réussie mais que la seconde échoue, vous devez libérer le premier bloc d’allocation avant de lancer l’exception. Si les deux allocations réussissent, vous pouvez procéder normalement et libérer les blocs en sortant de la fonction.

     - ou -

1. Utilisez une exception définie par l’utilisateur pour indiquer une condition problématique. Vous pouvez lancer un élément de n’importe quel type, même une classe entière, comme votre exception.

   L’exemple suivant tente de jouer un son à travers un dispositif d’onde et lance une exception s’il y a une défaillance.

   [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> La manipulation par défaut des exceptions par `CException` MFC ne `CException`s’applique qu’aux pointeurs sur les objets (et aux objets des classes dérivées). L’exemple ci-dessus contourne le mécanisme d’exception de MFC.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
