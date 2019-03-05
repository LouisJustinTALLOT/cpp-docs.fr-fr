---
title: ExitInstance, fonction membre
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: c76f588b22ad8ffd1d3dae954c5113feffb62a3f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279430"
---
# <a name="exitinstance-member-function"></a>ExitInstance, fonction membre

Le [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) fonction membre de classe [CWinApp](../mfc/reference/cwinapp-class.md) est appelée chaque fois qu’une copie de votre application se termine, généralement suite à l’utilisateur de quitter l’application.

Substituer `ExitInstance` si vous avez besoin de traitement de nettoyage spécial, telles que la libération des ressources de graphics device interface (GDI) ou de libération de mémoire utilisée pendant l’exécution du programme. Nettoyage des éléments standards tels que des documents et vues, toutefois, est fourni par l’infrastructure, d’autres fonctions substituables qui permet d’effectuer le nettoyage spécial spécifique à ces objets.

## <a name="see-also"></a>Voir aussi

[CWinApp : La classe d’Application](../mfc/cwinapp-the-application-class.md)
