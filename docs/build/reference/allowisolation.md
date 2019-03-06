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
ms.openlocfilehash: ac9d1f067259b092a261702b51f2355d4f908469
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417435"
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
