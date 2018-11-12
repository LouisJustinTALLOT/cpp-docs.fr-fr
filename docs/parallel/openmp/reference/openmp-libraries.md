---
title: Bibliothèques OpenMP
ms.date: 10/24/2018
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
ms.openlocfilehash: 75f772c953a2120a02f72d8bdfc73c1baaaef390
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530336"
---
# <a name="openmp-libraries"></a>Bibliothèques OpenMP

Décrit les fichiers .lib qui composent les bibliothèques d’exécution OpenMP dans Visual C++.

Les bibliothèques suivantes contiennent les fonctions de bibliothèque Runtime Visual C++ OpenMP.

|Bibliothèque du run-time OpenMP|Caractéristiques|
|------------------------------|---------------------|
|VCOMP. LIB|Lien dynamique, multithread (bibliothèque d’importation pour VCOMP. LIB).|
|VCOMPD. LIB|Lien dynamique, multithread (bibliothèque d’importation pour VCOMPD. COUVERCLE) (débogage)|

Si _DEBUG est défini dans une compilation et si `#include omp.h` est dans le code source, VCOMPD. LIB sera la bibliothèque par défaut. Sinon, VCOMP. LIB sera utilisé.

Vous pouvez utiliser [/NODEFAULTLIB (ignorer les bibliothèques)](../../../build/reference/nodefaultlib-ignore-libraries.md) à supprimer de la bibliothèque par défaut et lier explicitement avec la bibliothèque de votre choix.

Les DLL OpenMP se trouvent dans le répertoire de package redistribuable Visual C++ et doivent être distribués avec les applications qui utilisent OpenMP.

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque](openmp-library-reference.md)
