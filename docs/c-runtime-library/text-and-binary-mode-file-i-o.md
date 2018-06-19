---
title: E/S de fichier en mode texte et binaire | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4be1a3619fcd441dbcca53b0a1c369e30f9fb678
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411482"
---
# <a name="text-and-binary-mode-file-io"></a>E/S de fichier en mode texte et binaire

Les opérations d’E/S sur les fichiers ont lieu dans l’un des deux modes de translation (*text* ou *binary*), selon le mode dans lequel le fichier est ouvert. Les fichiers de données sont généralement traités en mode texte. Pour contrôler le mode de translation de fichier, vous pouvez :

- Conserver le paramètre de valeur par défaut actuel et spécifier le mode alternatif uniquement lorsque vous ouvrez les fichiers sélectionnés.

- Utiliser la fonction [_set_fmode](../c-runtime-library/reference/set-fmode.md) pour modifier le mode par défaut pour les nouveaux fichiers ouverts. Utiliser [_get_fmode](../c-runtime-library/reference/get-fmode.md) pour rechercher le mode par défaut en cours. Le paramètre par défaut est le mode texte (**_O_TEXT**).

- Modifiez le mode de traduction par défaut directement en définissant la variable globale [_fmode](../c-runtime-library/fmode.md) dans votre programme. La fonction **_set_fmode** définit la valeur de cette variable, mais elle peut également être définie directement.

Lorsque vous appelez une fonction d’ouverture de fichier telle que [_open](../c-runtime-library/reference/open-wopen.md), [fopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) ou [_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md), vous pouvez remplacer le paramètre par défaut actuel de **_fmode** en spécifiant l’argument approprié pour la fonction [_set_fmode](../c-runtime-library/reference/set-fmode.md). Par défaut, les flux **stdin**, **stdout** et **stderr** s’ouvrent toujours en mode texte. Vous pouvez également remplacer cette valeur par défaut lors de l’ouverture de ces fichiers. Utilisez [_setmode](../c-runtime-library/reference/setmode.md) pour modifier le mode de translation en utilisant le descripteur de fichier une fois que le fichier est ouvert.

## <a name="see-also"></a>Voir aussi

[Entrée et sortie](../c-runtime-library/input-and-output.md)<br/>
 [Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
