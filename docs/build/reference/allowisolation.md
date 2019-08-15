---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 359a68d5ec0a8c7390b5f0343530864e880a057c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493120"
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

**/ALLOWISOLATION: no** indique que les exécutables sont chargés comme s’il n’existait aucun manifeste, et provoque la référence `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` de [EDITBIN](editbin-reference.md) pour définir le bit `DllCharacteristics` dans le champ d’en-tête facultatif.

Quand l'isolation est désactivée pour un fichier exécutable, le chargeur Windows ne tente pas de trouver un manifeste d'application pour le processus nouvellement créé. Le nouveau processus n’a pas de contexte d’activation par défaut, même s’il existe un manifeste dans le fichier exécutable lui-même ou s’il existe un manifeste portant le nom *exécutable-Name*. exe. manifest.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)<br/>
[/ALLOWISOLATION (Recherche de manifeste)](allowisolation-manifest-lookup.md)<br/>
[Référence des fichiers manifeste](/windows/win32/SbsCs/manifest-files-reference)
