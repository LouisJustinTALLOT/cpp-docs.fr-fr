---
title: Avertissement de génération PRJ0029 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0029
dev_langs:
- C++
helpviewer_keywords:
- PRJ0029
ms.assetid: f02c09c6-09f3-4d44-8cd4-9a25336be1ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 854120bf6021295348ff2e28b36f7b44007017b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026006"
---
# <a name="project-build-warning-prj0029"></a>Avertissement de génération de projet PRJ0029

La propriété 'Sorties' de l’étape de génération personnalisée au niveau du projet n’est pas définie. L’étape de génération personnalisée va être ignorée.

Une étape de génération personnalisée n’a pas été exécutée car aucune sortie n’a été spécifié.

Pour résoudre cette erreur, procédez comme suit :

- Exclure l’étape de génération personnalisée de la génération.

- Ajouter une sortie.

- Supprimez le contenu de la commande de l’étape de génération personnalisée.