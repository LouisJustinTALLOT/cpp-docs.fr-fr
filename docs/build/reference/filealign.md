---
description: En savoir plus sur:/FILEALIGN (aligner les sections dans les fichiers)
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
ms.openlocfilehash: a67cf682c8fe55b80b2253864e08919e08242f74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192160"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN (Aligner les sections dans les fichiers)

L’option **/filealign** de l’éditeur de liens vous permet de spécifier l’alignement des sections écrites dans votre fichier de sortie sous la forme d’un multiple d’une taille spécifiée.

## <a name="syntax"></a>Syntaxe

> __/Filealign :__*taille*

### <a name="parameters"></a>Paramètres

*size*<br/>
Taille d’alignement de la section en octets, qui doit être une puissance de deux.

## <a name="remarks"></a>Notes

L’option **/filealign** permet à l’éditeur de liens d’aligner chaque section du fichier de sortie sur une limite qui est un multiple de la valeur de *taille* . Par défaut, l’éditeur de liens n’utilise pas une taille d’alignement fixe.

L’option **/filealign** peut être utilisée pour améliorer l’efficacité de l’utilisation du disque ou pour accélérer le chargement des pages à partir du disque. Une plus petite taille de section peut être utile pour les applications qui s’exécutent sur des périphériques plus petits ou pour conserver des téléchargements plus petits. L’alignement des sections sur le disque n’affecte pas l’alignement en mémoire.

Utilisez [DUMPBIN](dumpbin-reference.md) pour afficher des informations sur les sections de votre fichier de sortie.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **ligne de commande** dans le dossier **éditeur de liens** .

1. Tapez le nom de l’option **/filealign :** et la taille dans la zone **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
