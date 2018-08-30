---
title: Avertissement de génération PRJ0042 de projet | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0042
dev_langs:
- C++
helpviewer_keywords:
- PRJ0042
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 260da8ac336c640ea875610b2c62e6c42c7d335e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211348"
---
# <a name="project-build-warning-prj0042"></a>Avertissement de génération de projet PRJ0042

> La propriété' sorties' de l’étape de build personnalisée pour le fichier '*fichier*' n’est pas définie. L’étape de génération personnalisée va être ignorée.

Une étape de génération personnalisée n’a pas été exécutée car aucune sortie n’a été spécifié.

Pour résoudre cette erreur, procédez comme suit :

- Exclure l’étape de génération personnalisée de la génération.

- Ajouter une sortie.

- Supprimez le contenu de la commande de l’étape de génération personnalisée.