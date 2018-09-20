---
title: -ALLOWISOLATION | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07414c86663ea6143a471691b01e584cdc033258
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392825"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Spécifie un comportement pour la recherche de manifeste.

## <a name="syntax"></a>Syntaxe

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Notes

**/ ALLOWISOLATION** provoque le système d’exploitation et charger des manifestes.

**/ ALLOWISOLATION** est la valeur par défaut.

**/ALLOWISOLATION:no** indique que les fichiers exécutables sont chargés comme s’il n’y avait aucun manifeste et causes [référence EDITBIN](../../build/reference/editbin-reference.md) pour définir le `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit dans l’en-tête optional `DllCharacteristics` champ.

Quand l'isolation est désactivée pour un fichier exécutable, le chargeur Windows ne tente pas de trouver un manifeste d'application pour le processus nouvellement créé. Le nouveau processus n’a pas un contexte d’activation par défaut, même s’il existe un manifeste dans le fichier exécutable lui-même ou s’il existe un manifeste qui porte le nom *nom_exécutable*. exe.manifest.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](../../build/reference/editbin-options.md)<br/>
[/ALLOWISOLATION (Recherche de manifeste)](../../build/reference/allowisolation-manifest-lookup.md)<br/>
[Référence des fichiers manifeste](/windows/desktop/SbsCs/manifest-files-reference)