---
title: 1.1 Portée
ms.date: 11/04/2016
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
ms.openlocfilehash: f87f631ae2d36662daa2ece4790170c00c5cbeb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449203"
---
# <a name="11-scope"></a>1.1 Portée

Cette spécification couvre une parallélisation uniquement dirigé par l’utilisateur, où l’utilisateur spécifie explicitement les actions à entreprendre par le compilateur et le système d’exécution afin d’exécuter le programme en parallèle. Les implémentations OpenMP C et C++ n’êtes pas obligées de vérifier les dépendances, les conflits, des blocages, des conditions de concurrence ou autres problèmes qui résultent de l’exécution du programme incorrect. L’utilisateur est tenu de vous assurer que l’application en utilisant les constructions OpenMP C et C++ API s’exécute correctement. La parallélisation automatique généré par le compilateur et les directives du compilateur afin de faciliter ce type parallélisation ne sont pas couvertes dans ce document.