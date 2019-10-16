---
title: Référence de bibliothèque OpenMP
ms.date: 07/30/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: c63ae5ba7f04d8ee6bd02418792804373fa71e6b
ms.sourcegitcommit: 170f5de63b0fec8e38c252b6afdc08343f4243a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72348220"
---
# <a name="openmp-library-reference"></a>Référence de bibliothèque OpenMP

Fournit des liens vers des constructions utilisées dans l’API OpenMP.

L’implémentation C++ visuelle de la norme OpenMP comprend les constructions suivantes.

|Construction|Description|
|---------------|-----------------|
|[Directives](openmp-directives.md)|Fournit des liens vers les directives utilisées dans l’API OpenMP.|
|[Clauses](openmp-clauses.md)|Fournit des liens vers des clauses utilisées dans l’API OpenMP.|
|[Fonctions](openmp-functions.md)|Fournit des liens vers les fonctions utilisées dans l’API OpenMP.|
|[Variables d’environnement](openmp-environment-variables.md)|Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.|

Les fonctions C++ de la bibliothèque Runtime OpenMP Visual sont contenues dans les bibliothèques suivantes.

|Bibliothèque Runtime OpenMP|Caractéristiques|
|------------------------------|---------------------|
|VCOMP. LIB|Multithread, liaison dynamique, (bibliothèque d’importation pour VCOMP. LIB).|
|VCOMPD. LIB|Multithread, liaison dynamique, (bibliothèque d’importation pour VCOMPD. CAPOT) (débogage)|

Si _ DEBUG est défini dans une compilation et si `#include <omp.h>` est dans le code source, VCOMPD. LIB sera la bibliothèque par défaut, sinon, VCOMP. LIB sera utilisé.

Vous pouvez utiliser [/NODEFAULTLIB (ignorer les bibliothèques)](../../../build/reference/nodefaultlib-ignore-libraries.md) pour supprimer la bibliothèque par défaut et établir une liaison explicite avec la bibliothèque de votre choix.

Les dll OpenMP se trouvent dans le C++ répertoire redistribuable Visual et doivent être distribuées avec des applications qui utilisent OpenMP.

## <a name="see-also"></a>Voir aussi

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
