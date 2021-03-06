---
description: 'En savoir plus sur : comment le contrôle de compte d’utilisateur (UAC) affecte votre application'
title: Répercussions du contrôle de compte utilisateur sur votre application
ms.date: 11/19/2018
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 64196e0cac0a5b4edcf0b24fd95df2e5291ec45a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320064"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Répercussions du contrôle de compte utilisateur sur votre application

Le contrôle de compte d'utilisateur (UAC) est une fonctionnalité de Windows Vista dans laquelle les comptes d'utilisateurs ont des privilèges limités. Vous pouvez rechercher des informations détaillées concernant le contrôle de compte d'utilisateur sur les sites Web suivants :

- [Meilleures pratiques et recommandations pour les développeurs pour les applications dans un environnement de moindre privilège](/windows/win32/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>Génération de projets après l'activation du contrôle de compte d'utilisateur

Si vous générez un projet Visual Studio C++ sur Windows Vista avec UAC désactivé et que vous activez ultérieurement le contrôle de compte d’utilisateur, vous devez nettoyer et régénérer le projet pour qu’il fonctionne correctement.

## <a name="applications-that-require-administrative-privileges"></a>Applications qui requièrent des privilèges d'administrateur

Par défaut, l’éditeur de liens Visual C++ incorpore un fragment UAC dans le manifeste d’une application avec un niveau d’exécution `asInvoker` . Si votre application nécessite des privilèges d'administrateur pour s'exécuter correctement (par exemple, si elle modifie le nœud HKLM du Registre ou si elle écrit dans des zones protégées du disque, comme le répertoire Windows), vous devez modifier votre application.

La première option consiste à modifier le fragment UAC du manifeste pour changer le niveau d’exécution en *requireAdministrator*. L'application demande ensuite à l'utilisateur ses informations d'identification administratives avant de s'exécuter. Pour plus d’informations sur la façon de procéder, consultez [/MANIFESTUAC (incorpore les informations de contrôle de compte d’utilisateur dans le manifeste)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).

La deuxième option consiste à ne pas incorporer de fragment du contrôle de compte d'utilisateur dans le manifeste en spécifiant l'option de l'éditeur de liens `/MANIFESTUAC:NO`. Dans ce cas, votre application s'exécutera en mode virtualisé. Toute modification apportée au Registre ou au système de fichiers ne sera pas rendue persistante une fois que votre application est terminée.

L'organigramme suivant décrit comment votre application s'exécutera selon que le contrôle de compte d'utilisateur est activé et que l'application a un manifeste de contrôle de compte d'utilisateur ou pas :

![Comportement du chargeur Windows](media/uacflowchart.png "Comportement du chargeur Windows")

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques de sécurité](security-best-practices-for-cpp.md)
