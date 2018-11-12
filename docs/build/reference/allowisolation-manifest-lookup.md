---
title: /ALLOWISOLATION (Recherche de manifeste)
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 7b2cb4160a0d25aa65d2c5eb345ba1bc08b1c6b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428091"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Recherche de manifeste)

Spécifie un comportement pour la recherche de manifeste.

## <a name="syntax"></a>Syntaxe

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Notes

**/ALLOWISOLATION:no** indique les DLL sont chargées comme s’il n’a pas de manifeste et entraîne l’éditeur de liens définir le `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit dans l’en-tête optional `DllCharacteristics` champ.

**/ ALLOWISOLATION** provoque le système d’exploitation et charger des manifestes.

**/ ALLOWISOLATION** est la valeur par défaut.

Lors de l’isolation est désactivée pour un fichier exécutable, le chargeur Windows ne tente pas de trouver un manifeste d’application pour le processus qui vient d’être créé. Le nouveau processus n’aura pas un contexte d’activation par défaut, même s’il existe un manifeste à l’intérieur du fichier exécutable ou dans le même répertoire que le fichier exécutable avec le nom <em>nom_exécutable</em>**. exe.manifest**.

Pour plus d’informations, consultez [référence des fichiers manifeste](/windows/desktop/SbsCs/manifest-files-reference).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **le fichier manifeste** page de propriétés.

1. Modifier le **autoriser l’Isolation** propriété.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
