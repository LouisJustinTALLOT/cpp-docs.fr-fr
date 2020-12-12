---
description: En savoir plus sur:/ALLOWISOLATION (recherche de manifeste)
title: /ALLOWISOLATION (Recherche de manifeste)
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 659c908e4de910941ca71c9f40814608df19c6d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187219"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Recherche de manifeste)

Spécifie un comportement pour la recherche de manifeste.

## <a name="syntax"></a>Syntaxe

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Notes

**/ALLOWISOLATION : no** indique que les dll sont chargées comme s’il n’existait aucun manifeste et que l’éditeur de liens a défini le `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit dans le champ d’en-tête facultatif `DllCharacteristics` .

**/ALLOWISOLATION** fait en sorte que le système d’exploitation effectue des recherches et des chargements de manifeste.

**/ALLOWISOLATION** est la valeur par défaut.

Lorsque l’isolation est désactivée pour un fichier exécutable, le chargeur Windows ne tente pas de trouver un manifeste d’application pour le processus nouvellement créé. Le nouveau processus n’aura pas de contexte d’activation par défaut, même s’il existe un manifeste dans le fichier exécutable ou placé dans le même répertoire que le fichier exécutable avec name <em>executable-name</em>**. exe. manifest**.

Pour plus d’informations, consultez [référence des fichiers manifestes](/windows/win32/SbsCs/manifest-files-reference).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés  >    >  **fichier manifeste** de l’éditeur de liens propriétés de configuration.

1. Modifiez la propriété **autoriser l’isolation** .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
