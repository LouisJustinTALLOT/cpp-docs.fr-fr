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
ms.openlocfilehash: 584958ac51bdc491ad1bdd16117ecaad6e000ec7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321070"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Spécification d'options de ligne de commande MIDL)

Spécifie un fichier de réponse pour les options de ligne de commande MIDL

## <a name="syntax"></a>Syntaxe

> **/MIDL:\@**<em>file</em>

## <a name="arguments"></a>Arguments

*fichier*<br/>
Le nom du fichier qui contient [options de ligne de commande MIDL](/windows/desktop/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Notes

Toutes les options pour la conversion d’un fichier IDL dans un fichier TLB doivent être indiquées dans *fichier*; Options de ligne de commande MIDL ne peut pas être spécifiées sur la ligne de commande de l’éditeur de liens. Si /MIDL n’est pas spécifié, le compilateur MIDL sera appelé avec uniquement le nom de fichier IDL et aucune autre option.

Le fichier doit contenir une option de ligne de commande MIDL par ligne.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **IDL incorporé** page de propriétés.

1. Modifier le **commandes MIDL** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/IDLOUT (Nommer les fichiers de sortie MIDL)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (Ne pas traiter les attributs dans MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (Nommer le fichier .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Générer un programmes par attributs](../../windows/building-an-attributed-program.md)
