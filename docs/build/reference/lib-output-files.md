---
title: Fichiers de sortie LIB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23665897266bab87c71b8b3889688113fe8aa99a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720705"
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