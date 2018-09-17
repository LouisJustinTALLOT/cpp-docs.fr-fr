---
title: -MIDL (spécifier les Options de ligne de commande MIDL) | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs:
- C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce4c5159a66963268ae83e0c0adfdc082dfcc81c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706938"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Spécification d'options de ligne de commande MIDL)

Spécifie un fichier de réponse pour les options de ligne de commande MIDL

## <a name="syntax"></a>Syntaxe

> **/ MIDL :\@**<em>fichier</em>

## <a name="arguments"></a>Arguments

*fichier*<br/>
Le nom du fichier qui contient [options de ligne de commande MIDL](/windows/desktop/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Notes

Toutes les options pour la conversion d’un fichier IDL dans un fichier TLB doivent être indiquées dans *fichier*; Options de ligne de commande MIDL ne peut pas être spécifiées sur la ligne de commande de l’éditeur de liens. Si /MIDL n’est pas spécifié, le compilateur MIDL sera appelé avec uniquement le nom de fichier IDL et aucune autre option.

Le fichier doit contenir une option de ligne de commande MIDL par ligne.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

2. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **IDL incorporé** page de propriétés.

3. Modifier le **commandes MIDL** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)<br/>
[/IDLOUT (nommer les fichiers de sortie MIDL)](../../build/reference/idlout-name-midl-output-files.md)
[/IGNOREIDL (ne pas traiter les attributs dans MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)
[/TLBOUT (nom. Fichier TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)
[générer un programmes par attributs](../../windows/building-an-attributed-program.md)