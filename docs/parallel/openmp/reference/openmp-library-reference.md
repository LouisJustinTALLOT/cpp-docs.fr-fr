---
description: 'En savoir plus sur : informations de référence sur la bibliothèque OpenMP'
title: Référence de bibliothèque OpenMP
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: fa1f654835afef94b0e00f52bebb0b7300d205be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342359"
---
# <a name="openmp-library-reference"></a>Référence de bibliothèque OpenMP

Fournit des liens vers des constructions utilisées dans l’API OpenMP.

L’implémentation Visual C++ de la norme OpenMP comprend les constructions suivantes.

|Construction|Description|
|---------------|-----------------|
|[Directives](openmp-directives.md)|Fournit des liens vers les directives utilisées dans l’API OpenMP.|
|[Clauses](openmp-clauses.md)|Fournit des liens vers des clauses utilisées dans l’API OpenMP.|
|[Fonctions](openmp-functions.md)|Fournit des liens vers les fonctions utilisées dans l’API OpenMP.|
|[Variables d’environnement](openmp-environment-variables.md)|Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.|

Les Visual C++ fonctions de la bibliothèque Runtime OpenMP sont contenues dans les bibliothèques suivantes.

|Bibliothèque Runtime OpenMP|Caractéristiques|
|------------------------------|---------------------|
|VCOMP. LIB|Multithread, liaison dynamique (bibliothèque d’importation pour VCOMP140.DLL).|
|VCOMPD. LIB|Multithread, liaison dynamique (bibliothèque d’importation pour VCOMP140D.DLL) (débogage)|

Si _DEBUG est défini dans une compilation et si `#include <omp.h>` se trouve dans le code source, VCOMPD. LIB sera la bibliothèque par défaut, sinon, VCOMP. LIB sera utilisé.

Vous pouvez utiliser [/NODEFAULTLIB (ignorer les bibliothèques)](../../../build/reference/nodefaultlib-ignore-libraries.md) pour supprimer la bibliothèque par défaut et établir une liaison explicite avec la bibliothèque de votre choix.

Les dll OpenMP se trouvent dans le Visual C++ répertoire redistribuable et doivent être distribuées avec des applications qui utilisent OpenMP.

## <a name="see-also"></a>Voir aussi

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
