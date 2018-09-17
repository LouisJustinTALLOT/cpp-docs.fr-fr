---
title: Réutilisation de fichiers Inline | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, reusing NMAKE
- revising inline files
- NMAKE program, inline files
ms.assetid: d42dbffb-2cef-4ccb-9a1f-20b8ef81481c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37544db8076d40e638b6ddf6f340070298229149
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722460"
---
# <a name="reusing-inline-files"></a>Réutilisation de fichiers inline

Pour réutiliser un fichier inline, spécifiez <<*filename* où le fichier est défini et utilisé tout d’abord, puis réutiliser *filename* sans << plus loin dans le même ou d’une autre commande. Exécutez la commande pour créer le fichier inline avant de toutes les commandes qui utilisent le fichier.

## <a name="see-also"></a>Voir aussi

[Fichiers inline dans un makefile](../build/inline-files-in-a-makefile.md)