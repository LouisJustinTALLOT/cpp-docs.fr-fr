---
title: Répercussions du contrôle de compte utilisateur sur votre application
ms.date: 11/04/2016
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 336260ddc1c9da795478d5541af73d9801633843
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556960"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Répercussions du contrôle de compte utilisateur sur votre application

Le contrôle de compte d’utilisateur (UAC) est une fonctionnalité de Windows Vista dans laquelle les comptes d’utilisateurs ont des privilèges limités. Vous pouvez rechercher des informations détaillées concernant le contrôle de compte d'utilisateur sur les sites Web suivants :

- [Pratiques recommandées et directives pour des Applications dans un environnement de moindre privilège](/windows/desktop/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>Génération de projets après l'activation du contrôle de compte d'utilisateur

Si vous générez un projet Visual C++ sur Windows Vista avec le contrôle de compte d'utilisateur désactivé et que vous activez ultérieurement le contrôle de compte d'utilisateur, vous devez nettoyer et régénérer le projet pour qu'il fonctionne correctement.

## <a name="applications-that-require-administrative-privileges"></a>Applications qui requièrent des privilèges d'administrateur

Par défaut, l’éditeur de liens Visual C++ incorpore un fragment du contrôle dans le manifeste d’une application avec un niveau d’exécution `asInvoker`. Si votre application nécessite des privilèges d'administrateur pour s'exécuter correctement (par exemple, si elle modifie le nœud HKLM du Registre ou si elle écrit dans des zones protégées du disque, comme le répertoire Windows), vous devez modifier votre application.

La première option consiste à modifier le fragment du contrôle du manifeste pour modifier le niveau d’exécution à *requireAdministrator*. L'application demande ensuite à l'utilisateur ses informations d'identification administratives avant de s'exécuter. Pour savoir comment procéder, consultez [/MANIFESTUAC (informations UAC incorpore dans le manifeste)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).

La deuxième option consiste à ne pas incorporer de fragment du contrôle de compte d'utilisateur dans le manifeste en spécifiant l'option de l'éditeur de liens `/MANIFESTUAC:NO`. Dans ce cas, votre application s'exécutera en mode virtualisé. Toute modification apportée au Registre ou au système de fichiers ne sera pas rendue persistante une fois que votre application est terminée.

L'organigramme suivant décrit comment votre application s'exécutera selon que le contrôle de compte d'utilisateur est activé et que l'application a un manifeste de contrôle de compte d'utilisateur ou pas :

![Comportement du chargeur de Windows Vista](media/uacflowchart.png "UACflowchart")

## <a name="see-also"></a>Voir aussi

[Bonnes pratiques de sécurité](security-best-practices-for-cpp.md)
