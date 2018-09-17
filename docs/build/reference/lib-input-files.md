---
title: Fichiers d’entrée LIB | Microsoft Docs
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
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 952c3345234192e3798fea483d527cd3afec4bff
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702466"
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