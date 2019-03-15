---
title: /FUNCTIONPADMIN (Création d'une image corrigeable en mémoire)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: 699da3cea9914b5a10bdf769015d41c33936a902
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818620"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Création d'une image corrigeable en mémoire)

Prépare une image corrigeable en mémoire.

## <a name="syntax"></a>Syntaxe

> **/FUNCTIONPADMIN**[**:**_space_]

### <a name="arguments"></a>Arguments

*space*<br/>
La quantité de remplissage à ajouter au début de chaque fonction en octets. Sur x86 par défaut est 5 octets de remplissage et sur x64 par défaut est 6 octets. Une valeur doit être fournie avec d’autres cibles.

## <a name="remarks"></a>Notes

Pour l’éditeur de liens produire une image corrigeable en mémoire, les fichiers .obj doivent ont été compilés avec [/hotpatch (créer une Image corrigeable en mémoire)](hotpatch-create-hotpatchable-image.md).

Lorsque vous compilez et liez une image à l’aide d’un appel unique de cl.exe, **/hotpatch** implique **/functionpadmin**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez le **/FUNCTIONPADMIN** option **des Options supplémentaires**. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
