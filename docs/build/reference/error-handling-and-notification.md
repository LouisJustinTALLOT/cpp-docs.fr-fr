---
title: Gestion et notification des erreurs
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 7aae4d68b272a6c12233f283d4b263648062b7c1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418943"
---
# <a name="error-handling-and-notification"></a>Gestion et notification des erreurs

Pour plus d’informations sur la gestion des erreurs et de notification, consultez [présentation de la fonction d’assistance](understanding-the-helper-function.md).

Pour plus d’informations sur les fonctions de raccordement, consultez [définitions des structures et constantes](../../build/reference/structure-and-constant-definitions.md).

Si votre programme utilise la DLL à chargement différé, il doit gérer efficacement les erreurs dans la mesure où les défaillances qui se produisent pendant l’exécution du programme provoquent des exceptions non gérées. Gestion des défaillances se compose de deux parties :

Récupération par un raccordement.
Si votre code doit récupérer ou fournir une autre bibliothèque et/ou la routine en cas d’échec, un raccordement peut être fourni à la fonction d’assistance qui peut être fourni ou résoudre cette situation. La routine de raccordement doit retourner une valeur appropriée, afin que le traitement peut continuer (HINSTANCE ou FARPROC) ou 0 pour indiquer qu’une exception doit être levée. Elle peut également générer sa propre exception ou **longjmp** hors du hook. Il existe des raccordements de notification et des raccordements de défaillance.

Création de rapports via une exception.
Si tout ce qui est nécessaire pour la gestion de l’erreur est d’annuler la procédure, aucun crochet n’est nécessaire tant que le code utilisateur peut gérer l’exception.

Les rubriques suivantes traitent de notification et la gestion des erreurs :

- [Raccordements de notification](../../build/reference/notification-hooks.md)

- [Raccordements de défaillance](../../build/reference/failure-hooks.md)

- [Exceptions](../../build/reference/exceptions-c-cpp.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)
