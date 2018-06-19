---
title: / /FILEALIGN (alignement des sections dans les fichiers) | Documents Microsoft
ms.date: 10/23/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /filealign
dev_langs:
- C++
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a737801663a2c7c1e896166291a1635fbbe6c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373268"
---
# <a name="filealign-align-sections-in-files"></a>/ /FILEALIGN (alignement des sections dans les fichiers)

Le **/FILEALIGN** option de l’éditeur de liens vous permet de spécifier l’alignement des sections écrits dans votre fichier de sortie sous la forme d’un multiple de la taille spécifiée.

## <a name="syntax"></a>Syntaxe

> __/ /FILEALIGN :__*taille*

### <a name="parameters"></a>Paramètres

*size*  
La taille d’alignement de section en octets, qui doit être une puissance de deux.

## <a name="remarks"></a>Notes

Le **/FILEALIGN** option entraîne l’éditeur de liens aligner chaque section dans le fichier de sortie sur une limite qui est un multiple de la *taille* valeur. Par défaut, l’éditeur de liens n’utilise pas une taille fixe d’alignement.

Le **/FILEALIGN** option peut être utilisée pour améliorer l’efficacité de l’utilisation du disque, ou pour rendre la page se charge à partir du disque plus rapide. Une plus petite taille de section peut être utile pour les applications qui s’exécutent sur des périphériques de petite taille, ou bien pour conserver les téléchargements plus petits. Alignement des sections sur le disque n’affecte pas d’alignement en mémoire.

Utilisez [DUMPBIN](dumpbin-reference.md) pour afficher des informations sur les sections de votre fichier de sortie.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **ligne de commande** page de propriétés dans le **l’éditeur de liens** dossier.

1. Tapez le nom de l’option **/FILEALIGN :** et la taille de la **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
[Options de l’éditeur de liens](../../build/reference/linker-options.md)