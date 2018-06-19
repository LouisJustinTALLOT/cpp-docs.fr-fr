---
title: -IGNORE (ignorer les avertissements spécifiques) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /OVERWRITE
dev_langs:
- C++
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b096fc12f69fbe637a3067646c20f6d520a9250f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378007"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorer des avertissements spécifiques)
```  
/IGNORE:warning[,warning]  
```  
  
## <a name="parameters"></a>Paramètres  
 `warning`  
 Numéro d'avertissement de l'éditeur de liens à supprimer, dans la plage 4 000 à 4 999.  
  
## <a name="remarks"></a>Notes  
 Par défaut, LINK signale tous les avertissements. Spécifiez **/ignorer :** `warning` pour indiquer à l’éditeur de liens pour supprimer un numéro d’avertissement spécifiques. Pour ignorer plusieurs avertissements, séparez les numéros d'avertissements avec des virgules.  
  
 L'éditeur de liens ne permet pas d'ignorer certains avertissements. Ce tableau répertorie les avertissements qui ne sont pas supprimés par **/ignorer**:  
  
|Avertissement de l'éditeur de liens||  
|--------------------|-|  
|LNK4017|Instruction `keyword` non prise en charge pour la plateforme cible ; ignorée|  
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|option '`option`' non reconnue ; ignorée|  
|LNK4062|'`option`'non compatible avec'`architecture`' de l’ordinateur cible ; option ignorée|  
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|"`option1`" ignoré à cause de la spécification "`option2`"|  
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|'`function`' de point d'entrée n'est pas __stdcall avec des arguments de '`number`' octets ; l'image risque de ne pas s'exécuter|  
|LNK4088|image en cours de génération à cause de l'option /FORCE ; l'image risque de ne pas s'exécuter|  
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|aucun argument spécifié avec l'option '`option`' ; commutateur ignoré|  
|LNK4203|erreur lors de la lecture de la base de données '`filename`' du programme ; édition de liens des objets comme s'il n'y avait aucune information de débogage|  
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|'`filename`' manque d’informations de débogage pour référencer le module ; objet sera lié sans informations de débogage|  
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|'`filename`' il manque des informations de débogage en cours pour référencer le module ; objet sera lié sans informations de débogage|  
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|informations sur le type précompilé introuvables ; '`filename`' non lié ou remplacé ; édition de liens des objets comme s'il n'y avait aucune information de débogage|  
|LNK4207|'`filename`' compilé avec /Yc /Yu/Z7 ; Impossible de créer PDB ; recompilez avec /Zi ; objet de liaison comme si aucune information de débogage|  
|LNK4208|format PDB non compatible dans '`filename`' ; supprimez-le et régénérez ; édition de liens des objets comme s'il n'y avait aucune information de débogage|  
|LNK4209|informations de débogage endommagées ; recompilez le module ; édition de liens des objets comme s'il n'y avait aucune information de débogage|  
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` n'est plus pris en charge ; ignoré|  
|LNK4228|'`option`' non valide pour une DLL ; ignoré|  
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|directive /`directive` non valide rencontrée ; ignorée|  
  
 En règle générale, les avertissements de l'éditeur de liens qui ne peuvent pas être ignorés correspondent à des échecs de génération, des erreurs de ligne de commande ou des erreurs de configuration que vous devez corriger.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Dans le **l’éditeur de liens** dossier, sélectionnez le **ligne de commande** page de propriétés.  
  
3.  Modifier la **des Options supplémentaires** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.