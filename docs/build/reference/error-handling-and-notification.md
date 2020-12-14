---
description: 'En savoir plus sur : gestion et notification des erreurs'
title: Gestion et notification des erreurs
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 234d50d0b4a7e8b81874d1926ac056f8cba23376
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200986"
---
# <a name="error-handling-and-notification"></a>Gestion et notification des erreurs

Pour plus d’informations sur la gestion des erreurs et la notification, consultez [fonctionnement de la fonction d’assistance](understanding-the-helper-function.md).

Pour plus d’informations sur les fonctions de raccordement, consultez [définitions de structure et de constante](structure-and-constant-definitions.md).

Si votre programme utilise des dll à chargement différé, il doit gérer les erreurs de façon fiable, car les défaillances qui se produisent pendant l’exécution du programme entraînent des exceptions non gérées. La gestion des défaillances se compose de deux parties :

Récupération via un Hook.
Si votre code doit récupérer ou fournir une bibliothèque de remplacement et/ou une routine en cas d’échec, un raccordement peut être fourni à la fonction d’assistance qui peut fournir ou résoudre le problème. La routine de raccordement doit retourner une valeur appropriée, afin que le traitement puisse continuer (HINSTANCE ou FARPROC) ou 0 pour indiquer qu’une exception doit être levée. Elle peut également lever sa propre exception ou **longjmp** à partir du Hook. Il existe des raccordements de notification et des raccordements de défaillance.

Création de rapports par le biais d’une exception.
Si tout ce qui est nécessaire pour gérer l’erreur est d’abandonner la procédure, aucun raccordement n’est nécessaire tant que le code utilisateur peut gérer l’exception.

Les rubriques suivantes traitent de la gestion et de la notification des erreurs :

- [Raccordements de notification](notification-hooks.md)

- [Raccordements de défaillance](failure-hooks.md)

- [Exceptions](exceptions-c-cpp.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les dll Delay-Loaded](linker-support-for-delay-loaded-dlls.md)
