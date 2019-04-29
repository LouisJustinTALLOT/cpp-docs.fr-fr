---
title: Référence de bibliothèque OpenMP
ms.date: 03/20/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: 6f4bbeca54bff1fc44a3576362edca9c30926d5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362515"
---
# <a name="openmp-library-reference"></a>Référence de bibliothèque OpenMP

Fournit des liens vers les constructions utilisées dans l’API OpenMP.

L’implémentation Visual C++ de la norme OpenMP inclut les constructions suivantes.

|Construction|Description|
|---------------|-----------------|
|[Directives](openmp-directives.md)|Fournit des liens vers les directives utilisées dans l’API OpenMP.|
|[Clauses](openmp-directives.md)|Fournit des liens vers les clauses utilisées dans l’API OpenMP.|
|[Fonctions](openmp-functions.md)|Fournit des liens vers les fonctions utilisées dans l’API OpenMP.|
|[Variables d’environnement](openmp-environment-variables.md)|Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.|

L’élément visuel C++ fonctions de bibliothèque du run-time OpenMP sont contenues dans les bibliothèques suivantes.

|Bibliothèque du run-time OpenMP|Caractéristiques|
|------------------------------|---------------------|
|VCOMP.LIB|Lien dynamique, multithread (bibliothèque d’importation pour VCOMP. LIB).|
|VCOMPD.LIB|Lien dynamique, multithread (bibliothèque d’importation pour VCOMPD. COUVERCLE) (débogage)|

Si _DEBUG est défini dans une compilation et si `#include omp.h` est dans le code source, VCOMPD. LIB sera la valeur par défaut de lib, sinon, VCOMP. LIB sera utilisé.

Vous pouvez utiliser [/NODEFAULTLIB (ignorer les bibliothèques)](../../../build/reference/nodefaultlib-ignore-libraries.md) à supprimer de la bibliothèque par défaut et lier explicitement avec la bibliothèque de votre choix.

Les DLL OpenMP se trouvent dans le répertoire de package redistribuable Visual C++ et doivent être distribués avec les applications qui utilisent OpenMP.

## <a name="see-also"></a>Voir aussi

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)