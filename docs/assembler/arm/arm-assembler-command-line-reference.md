---
title: Informations de référence sur la ligne de commande de l’assembleur ARM
description: Guide de référence des options de ligne de commande de l’assembleur Microsoft ARM.
ms.date: 02/09/2020
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: a63273e8d21e7a28574ec79d62c15f29ee59cd50
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257377"
---
# <a name="arm-assembler-command-line-reference"></a>Informations de référence sur la ligne de commande de l’assembleur ARM

Cet article fournit des informations sur la ligne de commande de l’assembleur Microsoft ARM, **armasm**. **armasm** assemble le langage assembleur ARMv7 Thumb dans l’implémentation Microsoft du format COFF (Common Object File Format). L’éditeur de liens peut lier des objets de code COFF produits par l’assembleur ARM et le compilateur C. Elle peut être liée avec les bibliothèques d’objets créées par le générateur de bibliothèques.

## <a name="syntax"></a>Syntaxe

> **`armasm`** [*options*] *SOURCE_FILE* *object_file*\
> **`armasm`** [*options*] **`-o`** *object_file* *SOURCE_FILE*

### <a name="parameters"></a>Paramètres

*options*\
Une combinaison de zéro ou plusieurs des options suivantes :

- *nom de fichier*`-errors`\
   Rediriger les messages d’erreur et d’avertissement vers le *nom de fichier*.

- **`-i`** *dir*[ **`;`** <em>Rép</em>] \
   Ajoutez les répertoires spécifiés au chemin de recherche include.

- **`-predefine`** *directive*\
   Spécifiez une directive définis, SETL ou SETS pour prédéfinir un symbole. \
   Exemple : `armasm.exe -predefine "COUNT SETA 150" source.asm`\
   Pour plus d’informations, consultez le [Guide de référence Armasm du compilateur ARM](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

- **`-nowarn`**\
   Désactivez tous les messages d’avertissement.

- *Avertissement*`-ignore`\
   Désactive l’avertissement spécifié. Pour connaître les valeurs possibles, consultez la section à propos des avertissements.

- **`-help`**\
   Imprimez le message d’aide de la ligne de commande.

- \ de l' *ordinateur* **`-machine`**
   Spécifiez le type d’ordinateur à définir dans l’en-tête PE.  Les valeurs possibles pour l' *ordinateur* sont : \
   **ARM**: définit le type d’ordinateur sur IMAGE_FILE_MACHINE_ARMNT. Il s’agit de l’option par défaut. \
   **Thumb**: définit le type d’ordinateur sur IMAGE_FILE_MACHINE_THUMB.

- **`-oldit`**\
   Génère des blocs de style ARMv7.  Par défaut, les blocs informatiques compatibles ARMv8 sont générés.

- *nom de fichier*`-via`\
   Lire des arguments de ligne de commande supplémentaires à partir du *nom de fichier*.

- **`-16`**\
   Assemblez la source en tant qu’instructions Thumb 16 bits.  Cette option est celle par défaut.

- **`-32`**\
   Assemblez la source en tant qu’instructions ARM 32 bits.

- **`-g`**\
   Générer des informations de débogage.

- *option*`-errorReport:`\
   Cette fonction est déconseillée. À compter de Windows Vista, le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) .

*source_file*\
Nom du fichier source.

*object_file*\
Nom du fichier de l’objet (de sortie).

## <a name="remarks"></a>Notes

L’exemple suivant montre comment utiliser armasm dans un scénario classique. Tout d’abord, utilisez armasm pour générer un fichier de source de langage assembleur (. ASM) dans un fichier objet (. obj). Utilisez ensuite le compilateur C de la ligne de commande CL pour compiler un fichier source (. C) et spécifiez également l’option de l’éditeur de liens pour lier le fichier objet ARM.

```cmd
armasm myasmcode.asm -o myasmcode.obj
cl myccode.c /link myasmcode.obj
```

## <a name="see-also"></a>Voir aussi

\ des messages de diagnostic de l' [assembleur ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)
[Directives de l’assembleur ARM](../../assembler/arm/arm-assembler-directives.md)
