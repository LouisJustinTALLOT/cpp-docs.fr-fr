---
title: Fichiers d'entrée LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: fb0095bd9e8699fbc9a1a144833d12d2cf4a1f83
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423090"
---
# <a name="lib-input-files"></a>Fichiers d'entrée LIB

Les fichiers d’entrée attendus par LIB varient selon le mode dans lequel il est utilisé, comme indiqué dans le tableau suivant.

|Mode|Entrée|
|----------|-----------|
|Par défaut (création ou modification d’une bibliothèque)|Objet (.obj) fichiers, COFF bibliothèques (.lib), fichiers objet (.obj) de Format OMF (Object Model) 32 bits|
|Extraction d’un membre avec /EXTRACT|Bibliothèque COFF (.lib)|
|Création d’une exportation de fichier et de bibliothèque avec /DEF d’importation|Fichier de définition de module (.def), fichiers objets (.obj), COFF bibliothèques (.lib), les fichiers objet (.obj) OMF 32 bits|

> [!NOTE]
>  Bibliothèques OMF créés par la version 16 bits de LIB ne peut pas être utilisés en tant qu’entrée vers la version 32 bits de LIB.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de LIB](../../build/reference/overview-of-lib.md)
