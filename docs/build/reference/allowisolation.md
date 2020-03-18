---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 3dae8ee83e25492fab0ba2c6a55681728d5f3453
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440375"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Spécifie un comportement pour la recherche de manifeste.

## <a name="syntax"></a>Syntaxe

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Notes

**/ALLOWISOLATION** fait en sorte que le système d’exploitation effectue des recherches et des chargements de manifeste.

**/ALLOWISOLATION** est la valeur par défaut.

**/ALLOWISOLATION : no** indique que les fichiers exécutables sont chargés comme s’il n’existait aucun manifeste, et provoque la [référence de EDITBIN](editbin-reference.md) pour définir le bit d' `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` dans le champ `DllCharacteristics` de l’en-tête facultatif.

Quand l'isolation est désactivée pour un fichier exécutable, le chargeur Windows ne tente pas de trouver un manifeste d'application pour le processus nouvellement créé. Le nouveau processus n’a pas de contexte d’activation par défaut, même s’il existe un manifeste dans le fichier exécutable lui-même ou s’il existe un manifeste portant le nom *exécutable-Name*. exe. manifest.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)<br/>
[/ALLOWISOLATION (Recherche de manifeste)](allowisolation-manifest-lookup.md)<br/>
[Référence des fichiers manifeste](/windows/win32/SbsCs/manifest-files-reference)
