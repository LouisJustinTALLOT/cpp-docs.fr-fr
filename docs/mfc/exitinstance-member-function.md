---
title: ExitInstance, fonction membre
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: b1c5b3a20f25f909188023ab1650bc41316d7a9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637734"
---
# <a name="exitinstance-member-function"></a>ExitInstance, fonction membre

Le [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) fonction membre de classe [CWinApp](../mfc/reference/cwinapp-class.md) est appelée chaque fois qu’une copie de votre application se termine, généralement suite à l’utilisateur de quitter l’application.

Substituer `ExitInstance` si vous avez besoin de traitement de nettoyage spécial, telles que la libération des ressources de graphics device interface (GDI) ou de libération de mémoire utilisée pendant l’exécution du programme. Nettoyage des éléments standards tels que des documents et vues, toutefois, est fourni par l’infrastructure, d’autres fonctions substituables qui permet d’effectuer le nettoyage spécial spécifique à ces objets.

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)
