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
ms.openlocfilehash: 3f1b6526f51e5aaa48008792361d3e63249d9f16
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502848"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Spécification d'options de ligne de commande MIDL)

Spécifie un fichier réponse pour les options de ligne de commande MIDL

## <a name="syntax"></a>Syntax

> **/MIDL : \@ ** <em>fichier</em>

## <a name="arguments"></a>Arguments

*file*<br/>
Nom du fichier qui contient les [options de ligne de commande MIDL](/windows/win32/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Remarques

Toutes les options de conversion d’un fichier IDL en fichier TLB doivent être fournies dans le *fichier*; Les options de ligne de commande MIDL ne peuvent pas être spécifiées sur la ligne de commande de l’éditeur de liens. Si/MIDL n’est pas spécifié, le compilateur MIDL est appelé uniquement avec le nom de fichier IDL et aucune autre option.

Le fichier doit contenir une option de ligne de commande MIDL par ligne.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez les **Propriétés de configuration**  >  **Linker**  >  page de propriétés**IDL incorporé** .

1. Modifiez la propriété **commandes MIDL** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/IDLOUT (nommer les fichiers de sortie MIDL)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (ne pas traiter les attributs dans MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (nom. Fichier TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Générer un programmes par attributs](../../windows/attributes/cpp-attributes-com-net.md)
