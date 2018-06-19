---
title: Erreur irrécupérable RC1120 du compilateur de ressources | Documents Microsoft
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
ms.openlocfilehash: d117f7b106e14cde2def5477fab5ad0fc92a6411
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321933"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Erreur irrécupérable RC1120 du compilateur de ressources 
la mémoire, si nécessaire le nombre d’octets  
  
 Le compilateur de ressources a manqué d’espace pour les éléments qu’il stocke dans le segment de mémoire. Cela est généralement le résultat d’avoir trop de symboles.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Augmentez l’espace de fichier d’échange Windows. Pour plus d’informations sur l’augmentation de l’espace de fichier d’échange, consultez la mémoire virtuelle dans l’aide de Windows.  
  
2.  Éliminer inutiles les fichiers include, en particulier les `#define`fonction et les prototypes.  
  
3.  Fractionnez le fichier en cours en deux ou plusieurs fichiers et de les compiler séparément.  
  
4.  Supprimer d’autres programmes ou les pilotes en cours d’exécution dans le système, qui utilisent des quantités importantes de mémoire.