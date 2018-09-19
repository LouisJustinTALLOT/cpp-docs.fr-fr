---
title: Erreur irrécupérable RC1120 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f28e381d4eac0bfd1f010ef3919452635a1b96
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057000"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Erreur irrécupérable RC1120 du compilateur de ressources 

manque de mémoire nécessaire au nombre d’octets

Le compilateur de ressources a manqué d’espace pour les éléments qu’il stocke dans le tas. Cela est généralement le résultat d’avoir trop de symboles.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Augmentez l’espace de fichier d’échange Windows. Pour plus d’informations sur l’augmentation de l’espace de fichier d’échange, consultez la mémoire virtuelle dans l’aide de Windows.

1. Éliminer inutiles les fichiers include, en particulier les inutiles `#define`(fonction) et les prototypes.

1. Fractionner le fichier en cours en deux ou plusieurs fichiers et les compiler séparément.

1. Supprimez les autres programmes ou pilotes en cours d’exécution dans le système, ce qui pourrait être consomme une quantité importante de mémoire.