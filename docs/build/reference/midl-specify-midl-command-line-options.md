---
title: /MIDL (Spécification d'options de ligne de commande MIDL)
ms.date: 09/05/2018
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
ms.openlocfilehash: ca172428943d2446490eeb10741966f5e8c9ea85
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492719"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Spécification d'options de ligne de commande MIDL)

Spécifie un fichier réponse pour les options de ligne de commande MIDL

## <a name="syntax"></a>Syntaxe

> **/MIDL:\@** <em>fichier</em>

## <a name="arguments"></a>Arguments

*fichier*<br/>
Nom du fichier qui contient les [options de ligne de commande MIDL](/windows/win32/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Notes

Toutes les options de conversion d’un fichier IDL en fichier TLB doivent être fournies dans le *fichier*; Les options de ligne de commande MIDL ne peuvent pas être spécifiées sur la ligne de commande de l’éditeur de liens. Si/MIDL n’est pas spécifié, le compilateur MIDL est appelé uniquement avec le nom de fichier IDL et aucune autre option.

Le fichier doit contenir une option de ligne de commande MIDL par ligne.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez les **Propriétés** > deconfigurationpage de propriétés**IDL incorporé** . > 

1. Modifiez la propriété **commandes MIDL** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/IDLOUT (Nommer les fichiers de sortie MIDL)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (Ne pas traiter les attributs dans MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (Nommer le fichier .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Générer un programmes par attributs](../../windows/building-an-attributed-program.md)
