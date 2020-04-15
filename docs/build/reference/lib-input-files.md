---
title: Fichiers d'entrée LIB
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: de81f79eecf3fc73c02894747f4b97cb107cf892
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328229"
---
# <a name="lib-input-files"></a>Fichiers d'entrée LIB

Les fichiers d’entrée attendus par LIB dépendent du mode dans lequel il est utilisé, comme indiqué dans le tableau suivant.

|Mode|Entrée|
|----------|-----------|
|Défaut (construction ou modification d’une bibliothèque)|Fichiers d’objets COFF (.obj), COFF libraries (.lib), 32 bits Object Model Format (OMF) (.obj) fichiers|
|Extrait d’un membre avec /EXTRACT|Bibliothèque COFF (.lib)|
|Construire un fichier d’exportation et une bibliothèque d’importation avec /DEF|Fichier module-définition (.def), fichiers d’objets COFF (.obj), bibliothèques COFF (.lib), fichiers d’objets OMF 32 bits (.obj)|

> [!NOTE]
> Les bibliothèques OMF créées par la version 16 bits de LIB ne peuvent pas être utilisées comme entrée dans la version 32 bits de LIB.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de LIB](overview-of-lib.md)
