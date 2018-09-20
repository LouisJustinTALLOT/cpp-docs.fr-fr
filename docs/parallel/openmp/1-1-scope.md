---
title: 1.1 d’étendue | Microsoft Docs
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
ms.openlocfilehash: 81babf799860030f6d398f64b55ed65039de8649
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393528"
---
# <a name="11-scope"></a>1.1 Portée

Cette spécification couvre une parallélisation uniquement dirigé par l’utilisateur, où l’utilisateur spécifie explicitement les actions à entreprendre par le compilateur et le système d’exécution afin d’exécuter le programme en parallèle. Les implémentations OpenMP C et C++ n’êtes pas obligées de vérifier les dépendances, les conflits, des blocages, des conditions de concurrence ou autres problèmes qui résultent de l’exécution du programme incorrect. L’utilisateur est tenu de vous assurer que l’application en utilisant les constructions OpenMP C et C++ API s’exécute correctement. La parallélisation automatique généré par le compilateur et les directives du compilateur afin de faciliter ce type parallélisation ne sont pas couvertes dans ce document.