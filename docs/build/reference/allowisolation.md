---
description: En savoir plus sur:/ALLOWISOLATION
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 7d935bc122b5f32bb8f1193feae58b5fc61e7faa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179588"
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

**/ALLOWISOLATION : no** indique que les exécutables sont chargés comme s’il n’existait aucun manifeste, et provoque la [référence de EDITBIN](editbin-reference.md) pour définir le `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit dans le champ d’en-tête facultatif `DllCharacteristics` .

Quand l'isolation est désactivée pour un fichier exécutable, le chargeur Windows ne tente pas de trouver un manifeste d'application pour le processus nouvellement créé. Le nouveau processus n’a pas de contexte d’activation par défaut, même s’il existe un manifeste dans le fichier exécutable lui-même ou s’il existe un manifeste portant le nom *exécutable-Name*. exe. manifest.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)<br/>
[/ALLOWISOLATION (recherche de manifeste)](allowisolation-manifest-lookup.md)<br/>
[Référence des fichiers manifeste](/windows/win32/SbsCs/manifest-files-reference)
