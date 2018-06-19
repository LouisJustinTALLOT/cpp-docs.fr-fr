---
title: 1.1 étendue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48d14ec722299a9ff72ad5bab0a68cde5e00d6ad
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686800"
---
# <a name="11-scope"></a>1.1 Portée
Cette spécification couvre la parallélisation uniquement dirigées par l’utilisateur, dans laquelle l’utilisateur spécifie explicitement les actions à entreprendre par le compilateur et le système d’exécution afin d’exécuter le programme en parallèle. Implémentations OpenMP C et C++ ne sont pas requis pour rechercher les dépendances, est en conflit, des interblocages, des conditions de concurrence ou autres problèmes qui résultent de l’exécution du programme incorrect. L’utilisateur est chargé de s’assurer que l’application en utilisant les constructions OpenMP C et C++ API s’exécute correctement. La parallélisation automatique généré par le compilateur et les directives du compilateur pour faciliter ce type parallélisation ne sont pas traités dans ce document.