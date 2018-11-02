---
title: Fichiers de sortie LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
ms.openlocfilehash: bc505a9a946f564425513dad8107fd962eb054b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562897"
---
# <a name="lib-output-files"></a>Fichiers de sortie LIB

Les fichiers de sortie produits par LIB varient selon le mode dans lequel il est utilisé, comme indiqué dans le tableau suivant.

|Mode|Sortie|
|----------|------------|
|Par défaut (création ou modification d’une bibliothèque)|Bibliothèque COFF (.lib)|
|Extraction d’un membre avec /EXTRACT|Fichier objet (.obj)|
|Création d’une exportation de fichier et de bibliothèque avec /DEF d’importation|Bibliothèque d’importation (.lib) et fichier d’exportation (.exp)|

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de LIB](../../build/reference/overview-of-lib.md)