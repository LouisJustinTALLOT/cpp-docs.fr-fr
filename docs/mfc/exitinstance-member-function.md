---
title: ExitInstance, fonction membre
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: 58546d26293ad48a39a36b98ba4bfdabb68385ee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622696"
---
# <a name="exitinstance-member-function"></a>ExitInstance, fonction membre

La fonction membre [ExitInstance](reference/cwinapp-class.md#exitinstance) de la classe [CWinApp](reference/cwinapp-class.md) est appelée chaque fois qu’une copie de votre application se termine, généralement à la suite de la fermeture de l’application par l’utilisateur.

Remplacez `ExitInstance` si vous avez besoin d’un traitement de nettoyage spécial, par exemple la libération de ressources GDI (Graphics Device Interface) ou la désallocation de mémoire utilisée pendant l’exécution du programme. Toutefois, le nettoyage d’éléments standard, tels que les documents et les vues, est fourni par l’infrastructure, avec d’autres fonctions substituables pour effectuer un nettoyage spécial spécifique à ces objets.

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](cwinapp-the-application-class.md)
