---
description: En savoir plus sur:/PGD (spécifier la base de données pour les optimisations de Profile-Guided)
title: /PGD (Spécifier la base de données pour les optimisations guidées par profil)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: 7030ddaef33c6ee794c470df2c42c72d78555369
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225984"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Spécifier la base de données pour les optimisations guidées par profil)

**L’option/PGD est déconseillée.** À compter de Visual Studio 2015, préférez les options de l’éditeur de liens [/GENPROFILE ou/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) à la place. Cette option permet de spécifier le nom du fichier. pgd utilisé par le processus d’optimisation guidée par profil.

## <a name="syntax"></a>Syntaxe

> **/PGD :**_nom de fichier_

## <a name="argument"></a>Argument

*filename*<br/>
Spécifie le nom du fichier. pgd utilisé pour stocker des informations sur le programme en cours d’exécution.

## <a name="remarks"></a>Notes

Lors de l’utilisation de l’option désuetd [/LTCG : PGINSTRUMENT](ltcg-link-time-code-generation.md) , utilisez **/PGD** pour spécifier un nom ou un emplacement par défaut pour le fichier. pgd. Si vous ne spécifiez pas **/PGD**, le nom de base du fichier. pgd est le même que le nom de base du fichier de sortie (. exe ou. dll) et il est créé dans le même répertoire que celui à partir duquel le lien a été appelé.

Quand vous utilisez l’option Deprecated **: PGOPTIMIZE** déconseillée, utilisez l’option **/PGD** pour spécifier le nom du fichier. pgd à utiliser pour créer l’image optimisée. L’argument de *nom de fichier* doit correspondre au *nom de fichier* spécifié pour **/LTCG : PGINSTRUMENT**.

Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Modifiez la propriété **de base de données guidée par profil** . Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
