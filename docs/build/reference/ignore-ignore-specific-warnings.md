---
title: /IGNORE (ignorer des avertissements spécifiques)
ms.date: 11/04/2016
f1_keywords:
- /OVERWRITE
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
ms.openlocfilehash: 4ed87a1a12bea189f56545cf5256351a29977643
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040260"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorer des avertissements spécifiques)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Paramètres

*warning*<br/>
Numéro d'avertissement de l'éditeur de liens à supprimer, dans la plage 4 000 à 4 999.

## <a name="remarks"></a>Remarques

Par défaut, LINK signale tous les avertissements. Spécifiez **/ignore :** `warning` pour indiquer à l’éditeur de liens de supprimer un numéro d’avertissement spécifique. Pour ignorer plusieurs avertissements, séparez les numéros d'avertissements avec des virgules.

L'éditeur de liens ne permet pas d'ignorer certains avertissements. Ce tableau répertorie les avertissements qui ne sont pas supprimés par **/ignore**:

| Avertissement de l'éditeur de liens | Message |
|--------------------|-|
|LNK4017|Instruction `keyword` non prise en charge pour la plateforme cible ; ignorée|
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|option '`option`' non reconnue ; ignorée|
|LNK4062|« `option` » n’est pas compatible avec l' `architecture` ordinateur cible «»; option ignorée|
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|"`option1`" ignoré à cause de la spécification "`option2`"|
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|’`function`’ de point d’entrée n’est pas __stdcall avec des arguments de ’`number`’ octets ; l’image risque de ne pas s’exécuter|
|LNK4088|image en cours de génération à cause de l'option /FORCE ; l'image risque de ne pas s'exécuter|
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|aucun argument spécifié avec l’option ’`option`’ ; commutateur ignoré|
|LNK4203|erreur lors de la lecture de la base de données '`filename`' du programme ; édition de liens des objets comme s'il n'y avait aucune information de débogage|
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|' `filename` 'ne contient pas d’informations de débogage pour le module de référencement ; objet de liaison comme si aucune information de débogage|
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|' `filename` 'ne contient pas d’informations de débogage actuelles pour le module de référencement ; objet de liaison comme si aucune information de débogage|
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|informations sur le type précompilé introuvables ; '`filename`' non lié ou remplacé ; édition de liens des objets comme s'il n'y avait aucune information de débogage|
|LNK4207|« `filename` » a compilé/YC/Yu/Z7 ; impossible de créer le PDB ; RECOMPILE avec/Zi ; objet de liaison comme s’il n’y avait aucune information de débogage|
|LNK4208|format PDB non compatible dans '`filename`' ; supprimez-le et régénérez ; édition de liens des objets comme s'il n'y avait aucune information de débogage|
|LNK4209|informations de débogage endommagées ; recompilez le module ; édition de liens des objets comme s'il n'y avait aucune information de débogage|
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` n'est plus pris en charge ; ignoré|
|LNK4228|' `option` 'non valide pour une dll ; ignoré|
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|directive /`directive` non valide rencontrée ; ignorée|

En règle générale, les avertissements de l'éditeur de liens qui ne peuvent pas être ignorés correspondent à des échecs de génération, des erreurs de ligne de commande ou des erreurs de configuration que vous devez corriger.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le dossier de l' **éditeur de liens** , sélectionnez la page de propriétés **ligne de commande** .

1. Modifiez la propriété **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.
