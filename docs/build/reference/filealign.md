---
title: /FILEALIGN (Aligner les sections dans les fichiers)
ms.date: 10/23/2017
f1_keywords:
- /filealign
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
ms.openlocfilehash: 43cfdd6efb163013d05877e91c8375eb592295a9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814473"
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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **ligne de commande** page de propriétés dans le **l’éditeur de liens** dossier.

1. Tapez le nom de l’option **/FILEALIGN :** et la taille dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
