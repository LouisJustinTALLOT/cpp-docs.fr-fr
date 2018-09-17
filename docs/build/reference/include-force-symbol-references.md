---
title: -INCLUDE (forcer les références de symbole) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6528f6edc51a2dd01e8f91107827b570a44785de
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715778"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Forcer les références des symboles)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>Paramètres

*Symbole*<br/>
Spécifie un symbole à ajouter à la table de symboles.

## <a name="remarks"></a>Notes

L’option /INCLUDE indique à l’éditeur de liens pour ajouter un symbole spécifié à la table de symboles.

Pour spécifier plusieurs symboles, tapez une virgule (,), un point-virgule ( ;) ou un espace entre les noms de symboles. Sur la ligne de commande, spécifiez/INCLUDE :`symbol` une fois pour chaque symbole.

L’éditeur de liens résout `symbol` en ajoutant l’objet qui contient la définition du symbole au programme. Cette fonctionnalité est utile pour inclure un objet de bibliothèque qui ne serait sinon pas lié au programme.

Spécification d’un symbole avec cette option substitue à la suppression de ce symbole par [/OPT : REF](../../build/reference/opt-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **entrée** page de propriétés.

1. Modifier le **références des symboles forcées** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)