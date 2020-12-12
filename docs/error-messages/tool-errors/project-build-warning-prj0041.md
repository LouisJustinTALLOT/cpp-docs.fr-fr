---
description: 'En savoir plus sur : avertissement de génération de projet projet PRJ0041'
title: Avertissement de génération de projet PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: dc6b36e052d3402f047257a4bf0035d7ec30f92a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206446"
---
# <a name="project-build-warning-prj0041"></a>Avertissement de génération de projet PRJ0041

Impossible de trouver la dépendance manquante’Dependency’pour le fichier’file'. Votre projet peut toujours être généré, mais peut continuer à apparaître obsolète jusqu’à ce que ce fichier soit trouvé.

Un fichier (fichier de ressources ou fichier. idl/. ODL, par exemple) contenait une instruction include que le système de projet n’a pas pu résoudre.

Étant donné que le système de projet ne traite pas les instructions de préprocesseur (#if, par exemple), l’instruction incriminée peut ne pas faire partie de la Build.

Pour résoudre cet avertissement, supprimez tout le code inutile dans les fichiers. RC ou ajoutez des fichiers d’espace réservé portant le nom approprié.
