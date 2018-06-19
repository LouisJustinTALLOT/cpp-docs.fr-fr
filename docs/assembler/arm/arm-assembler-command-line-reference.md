---
title: Référence de ligne de commande de l’assembleur ARM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f196b4aad76c72233c179249386dbb42960b31a6
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054609"
---
# <a name="arm-assembler-command-line-reference"></a>Référence de la ligne de commande de l'assembleur ARM
Cet article fournit des informations de ligne de commande sur l’assembleur Microsoft ARM, *armasm*, qui compile le langage d’assembly ARMv7 Thumb dans l’implémentation Microsoft du fichier de Format COFF (Common Object). L’éditeur de liens peut lier le code COFF avec le code d’objet qui est généré par l’assembleur ARM ou par le compilateur C, ainsi que des bibliothèques d’objets qui sont créés par le Générateur de bibliothèques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### <a name="parameters"></a>Paramètres  
 `options`  
 -erreurs `filename`  
 Rediriger les erreurs et messages d’avertissement `filename`.  
  
 -i `dir[;dir]`  
 Ajoutez les répertoires spécifiés dans le chemin de recherche include.  
  
 -prédéfinir `directive`  
 Spécification d’une directive de jeu de NŒUDSUNE, SETL ou les jeux de prédéfinir un symbole. Exemple : **armasm.exe-prédéfinir source.asm de « COUNT jeu de NŒUDSUNE 150 »**. Pour plus d’informations, consultez la [guide des outils assembleur ARM](http://go.microsoft.com/fwlink/p/?linkid=246102).  
  
 -nowarn  
 Désactiver tous les messages d’avertissement.  
  
 -Ignorer `warning`  
 Désactiver l’avertissement spécifié. Pour les valeurs possibles, consultez la section sur les avertissements.  
  
 -aide  
 Imprimer le message d’aide en ligne de commande.  
  
 -ordinateur `machine`  
 Spécifiez le type de machine à définir dans l’en-tête PE.  Les valeurs possibles de `machine` sont :  
**ARM**: définit le type de machine à IMAGE_FILE_MACHINE_ARMNT. Il s'agit de la valeur par défaut.   
**THUMB**: définit le type de machine à IMAGE_FILE_MACHINE_THUMB.  
  
 -oldit  
 Générer le style ARMv7 blocs de l’informatique.  Par défaut, compatible avec ARMv8 informatique blocs sont générés.  
  
 -via `filename`  
 Lire les arguments de ligne de commande supplémentaires à partir de `filename`.  
  
 -16  
 Assembler source en tant qu’instructions de curseur de défilement de 16 bits.  Il s'agit de la valeur par défaut.  
  
 -32  
 Assembler source en tant qu’instructions ARM 32 bits.  
  
 -g  
 Générer des informations de débogage.  
  
 -errorReport : `option`  
 Spécifiez comment interne assembleur les erreurs sont signalées à Microsoft.  Les valeurs possibles de `option` sont :   
**aucun**: ne pas envoyer de rapports.   
**invite**, inviter l’utilisateur à envoyer des rapports immédiatement.   
**file d’attente**: invite l’utilisateur à envoyer des rapports à la prochaine ouverture de session d’administration. Il s'agit de la valeur par défaut.   
**envoyer**, envoyer automatiquement des rapports.  
  
 `sourcefile`  
 Le nom du fichier source.  
  
 `objectfile`  
 Le nom du fichier objet (sortie).  
  
 L’exemple suivant montre comment utiliser armasm dans un scénario classique. Tout d’abord, utilisez armasm pour créer un fichier source (.asm) en langage assembleur dans un fichier objet (.obj). Ensuite, le compilateur de ligne de commande C permet de compiler un fichier source (.c) et également spécifier l’option de l’éditeur de liens pour lier le fichier d’objet ARM.  
  
 **armasm myasmcode.asm -o myasmcode.obj**  
  
 **CL myccode.c /link myasmcode.obj**  
  
## <a name="see-also"></a>Voir aussi  
 [Messages de Diagnostic assembleur ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [Directive d’assembleur ARM](../../assembler/arm/arm-assembler-directives.md)