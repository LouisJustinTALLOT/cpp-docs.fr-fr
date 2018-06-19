---
title: Bibliothèques OpenMP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46bd287ff8a020a4d5d7775afdb12f5571d43294
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694769"
---
# <a name="openmp-libraries"></a>Bibliothèques OpenMP
Décrit les fichiers .lib qui composent les bibliothèques Runtime OpenMP dans Visual C++.  
  
 Les bibliothèques suivantes contiennent les fonctions de la bibliothèque Runtime Visual C++ OpenMP.  
  
|Bibliothèque OpenMP|Caractéristiques|  
|------------------------------|---------------------|  
|VCOMP. LIB|Lien multithread, dynamique (bibliothèque d’importation pour VCOMP. LIB).|  
|VCOMPD. LIB|Lien multithread, dynamique (bibliothèque d’importation pour VCOMPD. COUVERCLE) (débogage)|  
  
 Si _DEBUG est défini dans une compilation et si `#include omp.h` est dans le code source, VCOMPD. LIB sera lib par défaut. Dans le cas contraire, VCOMP. LIB sera utilisé.  
  
 Vous pouvez utiliser [/NODEFAULTLIB (ignorer les bibliothèques)](../../../build/reference/nodefaultlib-ignore-libraries.md) à supprimer de la bibliothèque par défaut et un lien explicite avec lib de votre choix.  
  
 Les DLL OpenMP se trouvent dans le répertoire de package redistribuable Visual C++ et doivent être distribués avec les applications qui utilisent OpenMP.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de la bibliothèque](../../../parallel/openmp/reference/openmp-library-reference.md)