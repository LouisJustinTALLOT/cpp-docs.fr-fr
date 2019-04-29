---
title: 'Erreur irrécupérable RC1120 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: eff46ddee118c3355e548c73220b407db0561e36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374249"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Erreur irrécupérable RC1120 du compilateur de ressources 

manque de mémoire nécessaire au nombre d’octets

Le compilateur de ressources a manqué d’espace pour les éléments qu’il stocke dans le tas. Cela est généralement le résultat d’avoir trop de symboles.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Augmentez l’espace de fichier d’échange Windows. Pour plus d’informations sur l’augmentation de l’espace de fichier d’échange, consultez la mémoire virtuelle dans l’aide de Windows.

1. Éliminer inutiles les fichiers include, en particulier les inutiles `#define`(fonction) et les prototypes.

1. Fractionner le fichier en cours en deux ou plusieurs fichiers et les compiler séparément.

1. Supprimez les autres programmes ou pilotes en cours d’exécution dans le système, ce qui pourrait être consomme une quantité importante de mémoire.