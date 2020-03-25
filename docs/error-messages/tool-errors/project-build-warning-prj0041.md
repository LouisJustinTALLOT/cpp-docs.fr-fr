---
title: Avertissement de génération de projet PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: bb6469b1daf193223a9b3361cc3e4bfb96d0c751
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191928"
---
# <a name="project-build-warning-prj0041"></a>Avertissement de génération de projet PRJ0041

Impossible de trouver la dépendance manquante’Dependency’pour le fichier’file'. Votre projet peut toujours être généré, mais peut continuer à apparaître obsolète jusqu’à ce que ce fichier soit trouvé.

Un fichier (fichier de ressources ou fichier. idl/. ODL, par exemple) contenait une instruction include que le système de projet n’a pas pu résoudre.

Étant donné que le système de projet ne traite pas les instructions de préprocesseur (#if, par exemple), l’instruction incriminée peut ne pas faire partie de la Build.

Pour résoudre cet avertissement, supprimez tout le code inutile dans les fichiers. RC ou ajoutez des fichiers d’espace réservé portant le nom approprié.
