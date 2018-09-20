---
title: Bibliothèques OpenMP | Microsoft Docs
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
ms.openlocfilehash: c9a4ccfefeaeb9446731027db44b849233bfefd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391213"
---
# <a name="openmp-libraries"></a>Bibliothèques OpenMP

Décrit les fichiers .lib qui composent les bibliothèques d’exécution OpenMP dans Visual C++.

Les bibliothèques suivantes contiennent les fonctions de bibliothèque Runtime Visual C++ OpenMP.

|Bibliothèque du run-time OpenMP|Caractéristiques|
|------------------------------|---------------------|
|VCOMP. LIB|Lien dynamique, multithread (bibliothèque d’importation pour VCOMP. LIB).|
|VCOMPD. LIB|Lien dynamique, multithread (bibliothèque d’importation pour VCOMPD. COUVERCLE) (débogage)|

Si _DEBUG est défini dans une compilation et si `#include omp.h` est dans le code source, VCOMPD. LIB sera la bibliothèque par défaut. Sinon, VCOMP. LIB sera utilisé.

Vous pouvez utiliser [/NODEFAULTLIB (Ignore Libraries)](../../../build/reference/nodefaultlib-ignore-libraries.md) à supprimer de la bibliothèque par défaut et lier explicitement avec la bibliothèque de votre choix.

Les DLL OpenMP se trouvent dans le répertoire de package redistribuable Visual C++ et doivent être distribués avec les applications qui utilisent OpenMP.

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque](../../../parallel/openmp/reference/openmp-library-reference.md)