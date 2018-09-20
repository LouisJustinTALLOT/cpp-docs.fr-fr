---
title: 'Exceptions : Levée d’Exceptions à partir de vos propres fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6ef86f54442031b4383e6a0b8cc6f57e4e53d58
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418422"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Exceptions : levée d'exceptions à partir de vos propres fonctions

Il est possible d’utiliser le paradigme de gestion des exceptions MFC uniquement pour intercepter les exceptions levées par les fonctions dans MFC ou d’autres bibliothèques. En plus d’intercepter les exceptions levées par le code de bibliothèque, vous pouvez lever des exceptions à partir de votre propre code si vous écrivez des fonctions qui peuvent rencontrer des conditions exceptionnelles.

Lorsqu’une exception est levée, l’exécution de la fonction active est arrêtée et qu’il accède directement à la **catch** bloc de l’image de l’exception la plus intérieure. Le mécanisme d’exception ignore le chemin d’accès de la sortie normale d’une fonction. Par conséquent, vous devez veiller à supprimer ces blocs de mémoire qui seraient supprimés dans une sortie normale.

#### <a name="to-throw-an-exception"></a>Pour lever une exception

1. Utilisez une des fonctions d’assistance MFC, telles que `AfxThrowMemoryException`. Ces fonctions lever un objet exception préalloué du type approprié.

     Dans l’exemple suivant, une fonction essaie d’allouer deux blocs de mémoire et lève une exception si l’allocation échoue :

     [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

     Si la première allocation échoue, vous pouvez simplement lever l’exception de mémoire. Si la première allocation réussite mais la deuxième échoue, vous devez libérer le premier bloc d’allocation avant de lever l’exception. Si les deux allocations réussissent, vous pouvez poursuivre normalement et libérer les blocs lors de la sortie de la fonction.

     - ou

1. Utilisez une exception définie par l’utilisateur pour indiquer un problème. Vous pouvez lever un élément de tout type, même dans une classe entière, comme votre exception.

     L’exemple suivant tente d’émettre un signal sonore via un périphérique wave et lève une exception s’il existe un échec.

     [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
>  De MFC gestion par défaut des exceptions s’applique uniquement aux pointeurs vers `CException` objets (et les objets de `CException`-classes dérivées). L’exemple ci-dessus ignore le mécanisme d’exception de MFC.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

