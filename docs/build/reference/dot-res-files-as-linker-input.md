---
title: . Fichiers res en tant qu’entrée de l’éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RES files as linker input
- .res files as linker input
- linking [C++], resource files
- resource files, linking
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a6a572013a29420670a2aef8c91c9c4bc64e871
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706301"
---
# <a name="res-files-as-linker-input"></a>Fichiers .res en tant qu'entrée de l'Éditeur de liens

Vous pouvez spécifier un fichier .res lors de la liaison d’un programme. Le fichier .res est créé par le compilateur de ressources (RC). LIEN convertit automatiquement les fichiers .res en COFF. L’outil CVTRES.exe doit être dans le même répertoire que LINK.exe ou dans un répertoire spécifié dans la variable d’environnement PATH.

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée LINK](../../build/reference/link-input-files.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)