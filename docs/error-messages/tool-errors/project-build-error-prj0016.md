---
title: Erreur de génération de projet PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: ada89b074fd8e0c2bfc75ba833e9c5966a145312
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616864"
---
# <a name="project-build-error-prj0016"></a>Erreur de génération de projet PRJ0016

Les paramètres de sécurité utilisateur empêchent la création du processus. Ces paramètres sont requis pour la génération.

Vous êtes connecté en tant qu’utilisateur qui ne dispose pas des autorisations nécessaires pour créer des processus à l’aide d’un processus. Vous devez modifier les niveaux d’autorisation pour ce compte d’utilisateur, ou contactez votre administrateur de compte.

Cette erreur peut également se produire si la valeur de la clé de Registre suivante :

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Pour résoudre cette erreur, supprimez la clé RestrictRun. Si cette clé de Registre est nécessaire, ajoutez **vcspawn.exe** à la liste des entrées dans la clé.

Une autre cause de cette erreur est que votre paramètre de stratégie n’inclut pas VCSpawn.exe sous la clé de Registre HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun comme programme Windows autorisé pour ce compte d’utilisateur.

Pour plus d’informations, consultez [adhérant aux paramètres de stratégie système](https://msdn.microsoft.com/library/aa372139), dans la section sur « Exécuter uniquement Windows applications autorisées ».