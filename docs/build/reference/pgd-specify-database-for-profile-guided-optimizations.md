---
title: /PGD (Spécifier la base de données pour les optimisations guidées par profil)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: 68d112c0a40289ba62e3fe5c37ae23f8f55f9209
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601290"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Spécifier la base de données pour les optimisations guidées par profil)

**L’option /PGD est déconseillée.** À compter de Visual Studio 2015, préférez la [/GENPROFILE ou /fastgenprofile.](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) options de l’éditeur de liens à la place. Cette option est utilisée pour spécifier le nom du fichier .pgd utilisé par le processus d’optimisation guidée par profil.

## <a name="syntax"></a>Syntaxe

> **/ PGD :**_nom de fichier_

## <a name="argument"></a>Argument

*filename*<br/>
Spécifie le nom du fichier .pgd qui permet de conserver des informations sur le programme en cours d’exécution.

## <a name="remarks"></a>Notes

Lorsque vous utilisez déconseillées [/LTCG : PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md) , utilisez l’option **/PGD** pour spécifier un nom de non défini par défaut ou un emplacement pour le fichier .pgd. Si vous ne spécifiez pas **/PGD**, le nom de base du fichier .pgd est le même que le nom fichier de sortie (.exe ou .dll) base et est créé dans le même répertoire que celui à partir duquel le lien a été appelé.

Lorsque vous utilisez déconseillées **/LTCG : PGOPTIMIZE** option, utilisez le **/PGD** option pour spécifier le nom du fichier .pgd à utiliser pour créer l’image optimisée. Le *filename* l’argument doit correspondre à la *filename* spécifié à **/LTCG : PGINSTRUMENT**.

Pour plus d’informations, consultez [optimisation guidée par profil](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **optimisation** page de propriétés.

1. Modifier le **base de données guidée par profil** propriété. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)<br/>
