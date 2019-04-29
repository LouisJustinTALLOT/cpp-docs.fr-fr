---
title: Avertissement de génération de projet PRJ0042
ms.date: 08/27/2018
f1_keywords:
- PRJ0042
helpviewer_keywords:
- PRJ0042
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
ms.openlocfilehash: c91e40b6ad56d6201fc7d0ba7c9fbf23e620e8b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297745"
---
# <a name="project-build-warning-prj0042"></a>Avertissement de génération de projet PRJ0042

> La propriété' sorties' de l’étape de build personnalisée pour le fichier '*fichier*' n’est pas définie. L’étape de génération personnalisée va être ignorée.

Une étape de génération personnalisée n’a pas été exécutée car aucune sortie n’a été spécifié.

Pour résoudre cette erreur, procédez comme suit :

- Exclure l’étape de génération personnalisée de la génération.

- Ajouter une sortie.

- Supprimez le contenu de la commande de l’étape de génération personnalisée.