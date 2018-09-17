---
title: /FILEALIGN (Aligner les sections dans les fichiers) | Microsoft Docs
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
ms.openlocfilehash: 630fe7014c87487a9b4df61de60ac8f5518593e0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720016"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN (Aligner les sections dans les fichiers)

Le **/FILEALIGN** option de l’éditeur de liens vous permet de spécifier l’alignement des sections écrit dans votre fichier de sortie sous la forme d’un multiple d’une taille spécifiée.

## <a name="syntax"></a>Syntaxe

> __/ /FILEALIGN :__*taille*

### <a name="parameters"></a>Paramètres

*size*<br/>
La taille d’alignement de section en octets, qui doit être une puissance de deux.

## <a name="remarks"></a>Notes

Le **/FILEALIGN** option entraîne l’éditeur de liens aligner chaque section dans le fichier de sortie sur une limite qui est un multiple de la *taille* valeur. Par défaut, l’éditeur de liens n’utilise pas une taille fixe d’alignement.

Le **/FILEALIGN** option peut être utilisée afin d’optimiser l’utilisation du disque, ou pour rendre la page se charge à partir du disque plus rapide. Une plus petite taille de la section peut être utile pour les applications qui s’exécutent sur des appareils plus petits, ou bien pour conserver les téléchargements plus petits. Alignement des sections sur le disque n’affecte pas l’alignement en mémoire.

Utilisez [DUMPBIN](dumpbin-reference.md) pour afficher des informations sur les sections de votre fichier de sortie.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **ligne de commande** page de propriétés dans le **l’éditeur de liens** dossier.

1. Tapez le nom de l’option **/FILEALIGN :** et la taille dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)