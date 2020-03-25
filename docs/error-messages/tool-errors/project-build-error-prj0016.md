---
title: Erreur de génération de projet PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 0cab1e35a36ab78426923d60acafb5cdf2942469
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192742"
---
# <a name="project-build-error-prj0016"></a>Erreur de génération de projet PRJ0016

Les paramètres de sécurité de l’utilisateur empêchent la création du processus. Ces paramètres sont requis pour la génération.

Vous êtes connecté en tant qu’utilisateur qui ne dispose pas des autorisations nécessaires pour créer des processus à l’aide d’un processus. Vous devez modifier les niveaux d’autorisation pour ce compte d’utilisateur ou contacter votre administrateur de compte.

Cette erreur peut également se produire si la clé de Registre suivante est définie :

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Pour résoudre cette erreur, supprimez la clé RestrictRun. Si cette clé de Registre est nécessaire, ajoutez **vcspawn. exe** à la liste des entrées de la clé.

Une autre cause de cette erreur est que votre paramètre de stratégie n’inclut pas VCSpawn. exe sous la clé de Registre HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun comme programme de fenêtre autorisé pour ce compte d’utilisateur.

Pour plus d’informations, consultez la section relative [à l’adhésion aux paramètres de stratégie système](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings)dans la section « exécuter uniquement les applications Windows autorisées ».
