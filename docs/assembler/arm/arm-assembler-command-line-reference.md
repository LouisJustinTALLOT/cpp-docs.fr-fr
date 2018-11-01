---
title: Référence de la ligne de commande de l'assembleur ARM
ms.date: 08/30/2018
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: f49b59a81fbe5f11c0f219d1e1fe83a4ee811c7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579233"
---
# <a name="arm-assembler-command-line-reference"></a>Référence de la ligne de commande de l'assembleur ARM

Cet article fournit des informations de ligne de commande sur l’assembleur Microsoft ARM, *armasm*, qui compile le langage d’assembly ARMv7 Thumb dans l’implémentation Microsoft du fichier de Format COFF (Common Object). L’éditeur de liens peut lier le code COFF avec le code d’objet qui est généré par l’assembleur ARM ou par le compilateur C, ainsi que des bibliothèques d’objets qui sont créés par le Générateur de bibliothèques.

## <a name="syntax"></a>Syntaxe

> **armasm** [*options*] *sourcefile* *objectfile*
> **armasm** [*options *] **-o** *objectfile* *sourcefile*

### <a name="parameters"></a>Paramètres

*options*<br/>
Une combinaison de zéro ou plusieurs des opérations suivantes :

- **-erreurs** *nom de fichier*<br/>
   Rediriger les messages d’erreur et avertissement à *filename*.

- **i -** *dir*[**;** <em>dir</em>]<br/>
   Ajouter les répertoires spécifiés dans le chemin de recherche include.

- **-prédéfinir** *(directive)*<br/>
   Spécifiez une directive définis, SETL ou les jeux de prédéfinir un symbole.<br/>
   Exemple : **armasm.exe-prédéfinir source.asm « COUNT définis 150 »**<br/>
   Pour plus d’informations, consultez le [du compilateur ARM armasm Guide de référence](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

- **-nowarn**<br/>
   Désactiver tous les messages d’avertissement.

- **-Ignorer** *avertissement*<br/>
   Désactiver l’avertissement spécifié. Pour connaître les valeurs possibles, consultez la section sur les avertissements.

- **-help**<br/>
   Imprimer le message d’aide en ligne de commande.

- **-machine** *machine*<br/>
   Spécifier le type de machine à définir dans l’en-tête PE.  Les valeurs possibles pour *machine* sont :<br/>
   **ARM**: définit le type de machine à IMAGE_FILE_MACHINE_ARMNT. Il s'agit de la valeur par défaut.<br/>
   **THUMB**: définit le type de machine à IMAGE_FILE_MACHINE_THUMB.

- **-oldit**<br/>
   Générer un style ARMv7 blocs de l’informatique.  Par défaut, et ARMv8 compatibles informatique blocs sont générés.

- **-via** *nom de fichier*<br/>
   Lire les arguments de ligne de commande supplémentaires à partir de *filename*.

- **-16**<br/>
   Assemblez source en tant qu’instructions de curseur de défilement de 16 bits.  Il s'agit de la valeur par défaut.

- **-32**<br/>
   Assemblez source en tant qu’instructions ARM de 32 bits.

- **-g**<br/>
   Générer des informations de débogage.

- **-errorReport :** *option*<br/>
   Spécifiez comment interne assembleur erreurs sont signalées à Microsoft.  Les valeurs possibles pour *option* sont :<br/>
   **aucun**: ne pas envoyer de rapports.<br/>
   **invite**, inviter l’utilisateur d’envoyer immédiatement des rapports.<br/>
   **file d’attente**: inviter l’utilisateur à envoyer des rapports à la prochaine connexion de l’administrateur. Il s'agit de la valeur par défaut.<br/>
   **envoyer**, envoyer automatiquement des rapports.

*SourceFile*<br/>
Le nom du fichier source.

*objectfile*<br/>
Le nom du fichier objet (sortie).

## <a name="remarks"></a>Notes

L’exemple suivant montre comment utiliser armasm dans un scénario classique. Tout d’abord, utilisez armasm pour créer un fichier de source (.asm) de langage d’assembly vers un fichier objet (.obj). Ensuite, utilisez le compilateur de ligne de commande C pour compiler un fichier source (.c) et également spécifier l’option de l’éditeur de liens pour lier le fichier d’objet ARM.

**armasm myasmcode.asm -o myasmcode.obj**

**CL myccode.c /link myasmcode.obj**

## <a name="see-also"></a>Voir aussi

[Messages de diagnostic de l’assembleur ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
[Directive d’assembleur ARM](../../assembler/arm/arm-assembler-directives.md)<br/>
