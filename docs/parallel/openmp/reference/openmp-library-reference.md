---
title: Référence de bibliothèque OpenMP
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: b61eb356b782b3cd17557827734a706e0761a2a8
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810739"
---
# <a name="openmp-library-reference"></a>Référence de bibliothèque OpenMP

Fournit des liens vers des constructions utilisées dans l’API OpenMP.

L’implémentation C++ visuelle de la norme OpenMP comprend les constructions suivantes.

|Construire|Description|
|---------------|-----------------|
|[Directives](openmp-directives.md)|Fournit des liens vers les directives utilisées dans l’API OpenMP.|
|[Clauses](openmp-clauses.md)|Fournit des liens vers des clauses utilisées dans l’API OpenMP.|
|[Fonctions](openmp-functions.md)|Fournit des liens vers les fonctions utilisées dans l’API OpenMP.|
|[Variables d’environnement](openmp-environment-variables.md)|Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.|

Les fonctions C++ de la bibliothèque Runtime OpenMP Visual sont contenues dans les bibliothèques suivantes.

|Bibliothèque Runtime OpenMP|Caractéristiques|
|------------------------------|---------------------|
|VCOMP. LIB|Multithread, liaison dynamique, (bibliothèque d’importation pour VCOMP140. DLL).|
|VCOMPD. LIB|Multithread, liaison dynamique, (bibliothèque d’importation pour VCOMP140D. DLL) (débogage)|

Si _DEBUG est défini dans une compilation et si `#include <omp.h>` se trouve dans le code source, VCOMPD. LIB sera la bibliothèque par défaut, sinon, VCOMP. LIB sera utilisé.

Vous pouvez utiliser [/NODEFAULTLIB (ignorer les bibliothèques)](../../../build/reference/nodefaultlib-ignore-libraries.md) pour supprimer la bibliothèque par défaut et établir une liaison explicite avec la bibliothèque de votre choix.

Les dll OpenMP se trouvent dans le C++ répertoire redistribuable Visual et doivent être distribuées avec des applications qui utilisent OpenMP.

## <a name="see-also"></a>Voir aussi

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
