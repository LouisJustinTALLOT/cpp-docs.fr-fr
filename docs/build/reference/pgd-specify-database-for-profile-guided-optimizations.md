---
title: /PGD (Spécifier la base de données pour les optimisations guidées par profil)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: e1d7c9fcb94a9351ce94b66e04b4bfc523248f4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319796"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Spécifier la base de données pour les optimisations guidées par profil)

**L’option /PGD est déconseillée.** À compter de Visual Studio 2015, préférez la [/GENPROFILE ou /fastgenprofile.](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) options de l’éditeur de liens à la place. Cette option est utilisée pour spécifier le nom du fichier .pgd utilisé par le processus d’optimisation guidée par profil.

## <a name="syntax"></a>Syntaxe

> **/ PGD :**_nom de fichier_

## <a name="argument"></a>Argument

*filename*<br/>
Spécifie le nom du fichier .pgd qui permet de conserver des informations sur le programme en cours d’exécution.

## <a name="remarks"></a>Notes

Lorsque vous utilisez déconseillées [/LTCG : PGINSTRUMENT](ltcg-link-time-code-generation.md) , utilisez l’option **/PGD** pour spécifier un nom de non défini par défaut ou un emplacement pour le fichier .pgd. Si vous ne spécifiez pas **/PGD**, le nom de base du fichier .pgd est le même que le nom fichier de sortie (.exe ou .dll) base et est créé dans le même répertoire que celui à partir duquel le lien a été appelé.

Lorsque vous utilisez déconseillées **/LTCG : PGOPTIMIZE** option, utilisez le **/PGD** option pour spécifier le nom du fichier .pgd à utiliser pour créer l’image optimisée. Le *filename* l’argument doit correspondre à la *filename* spécifié à **/LTCG : PGINSTRUMENT**.

Pour plus d’informations, consultez [optimisations guidées par profil](../profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **optimisation** page de propriétés.

1. Modifier le **base de données guidée par profil** propriété. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
