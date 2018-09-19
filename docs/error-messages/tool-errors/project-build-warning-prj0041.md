---
title: Avertissement de génération PRJ0041 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7677c5718783065f64e52f98f7ddbed76e905d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038137"
---
# <a name="project-build-warning-prj0041"></a>Avertissement de génération de projet PRJ0041

Impossible de trouver manquant dépendance « dépendance » pour le fichier 'fichier'. Votre projet peut être généré, mais peut sembler obsolète tant que ce fichier se trouve.

Un fichier (fichier de ressources ou.idl/.odl, par exemple, contenait une instruction include que le système de projet n’a pas pu résoudre.

Étant donné que le système de projet ne traite pas les instructions de préprocesseur (#if, par exemple), l’instruction en fait peut-être pas partie de la build.

Pour résoudre cet avertissement, supprimez tout code inutile dans les fichiers .rc ou ajoutez des fichiers d’espace réservé du nom approprié.