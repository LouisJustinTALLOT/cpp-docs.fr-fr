---
description: 'En savoir plus sur : exceptions : levée d’exceptions à partir de vos propres fonctions'
title: "Exceptions : levée d'exceptions à partir de vos propres fonctions"
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 5a9d789680eeba218370471b1259c8c664f3c3cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290464"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Exceptions : levée d'exceptions à partir de vos propres fonctions

Il est possible d’utiliser le paradigme de gestion des exceptions MFC uniquement pour intercepter les exceptions levées par les fonctions dans MFC ou d’autres bibliothèques. En plus d’intercepter les exceptions levées par le code de bibliothèque, vous pouvez lever des exceptions à partir de votre propre code si vous écrivez des fonctions qui peuvent rencontrer des conditions exceptionnelles.

Lorsqu’une exception est levée, l’exécution de la fonction active est arrêtée et passe directement au **`catch`** bloc du frame d’exception le plus profond. Le mécanisme d’exception contourne le chemin de sortie normal d’une fonction. Par conséquent, vous devez être sûr de supprimer les blocs de mémoire qui seraient supprimés dans une sortie normale.

#### <a name="to-throw-an-exception"></a>Pour lever une exception

1. Utilisez l’une des fonctions d’assistance MFC, telles que `AfxThrowMemoryException` . Ces fonctions lèvent un objet exception préalloué du type approprié.

   Dans l’exemple suivant, une fonction tente d’allouer deux blocs de mémoire et lève une exception si l’une des allocations échoue :

   [!code-cpp[NVC_MFCExceptions#17](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Si la première allocation échoue, vous pouvez simplement lever l’exception de mémoire. Si la première allocation réussit mais que la deuxième échoue, vous devez libérer le premier bloc d’allocation avant de lever l’exception. Si les deux allocations réussissaient, vous pouvez continuer normalement et libérer les blocs lors de la sortie de la fonction.

     - ou -

1. Utilisez une exception définie par l’utilisateur pour indiquer une condition de problème. Vous pouvez lever un élément de n’importe quel type, même une classe entière, comme exception.

   L’exemple suivant tente de lire un son sur un appareil Wave et lève une exception en cas d’échec.

   [!code-cpp[NVC_MFCExceptions#18](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> La gestion par défaut des exceptions de MFC s’applique uniquement aux pointeurs vers `CException` des objets (et des objets de `CException` classes dérivées de). L’exemple ci-dessus ignore le mécanisme d’exception de MFC.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
