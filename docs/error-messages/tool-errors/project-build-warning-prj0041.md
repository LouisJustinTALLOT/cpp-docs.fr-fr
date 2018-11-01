---
title: Avertissement de génération de projet PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: b0fceff05ffe35515965b7e0a880c8b4c941b07e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583207"
---
# <a name="project-build-warning-prj0041"></a>Avertissement de génération de projet PRJ0041

Impossible de trouver manquant dépendance « dépendance » pour le fichier 'fichier'. Votre projet peut être généré, mais peut sembler obsolète tant que ce fichier se trouve.

Un fichier (fichier de ressources ou.idl/.odl, par exemple, contenait une instruction include que le système de projet n’a pas pu résoudre.

Étant donné que le système de projet ne traite pas les instructions de préprocesseur (#if, par exemple), l’instruction en fait peut-être pas partie de la build.

Pour résoudre cet avertissement, supprimez tout code inutile dans les fichiers .rc ou ajoutez des fichiers d’espace réservé du nom approprié.