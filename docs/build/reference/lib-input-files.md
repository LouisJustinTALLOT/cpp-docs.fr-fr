---
description: 'En savoir plus sur : fichiers d’entrée LIB'
title: Fichiers d'entrée LIB
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: f40cba91f0772e0073daca20a8f2093f3eec8aec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199543"
---
# <a name="lib-input-files"></a>Fichiers d'entrée LIB

Les fichiers d’entrée attendus par LIB dépendent du mode dans lequel il est utilisé, comme indiqué dans le tableau suivant.

|Mode|Entrée|
|----------|-----------|
|Par défaut (création ou modification d’une bibliothèque)|Fichiers objets (. obj) COFF, bibliothèques COFF (. lib), fichiers objets OMF (32-bit Object Model format)|
|Extraction d’un membre avec/EXTRACT|Bibliothèque COFF (. lib)|
|Génération d’un fichier d’exportation et d’une bibliothèque d’importation avec/DEF|Fichier de définition de module (. def), fichiers objets COFF (. obj), bibliothèques COFF (. lib), fichiers objets OMF 32 bits (. obj)|

> [!NOTE]
> Les bibliothèques OMF créées par la version 16 bits de LIB ne peuvent pas être utilisées en tant qu’entrée dans la version 32 bits de LIB.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble de LIB](overview-of-lib.md)
