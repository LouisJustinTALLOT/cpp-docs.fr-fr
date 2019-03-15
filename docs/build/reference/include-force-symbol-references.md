---
title: /INCLUDE (Forcer les références des symboles)
ms.date: 11/04/2016
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
ms.openlocfilehash: 1f7a443e32ed20550e3017c7e6ce70f4adf5137d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810976"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Forcer les références des symboles)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>Paramètres

*symbol*<br/>
Spécifie un symbole à ajouter à la table de symboles.

## <a name="remarks"></a>Notes

L’option /INCLUDE indique à l’éditeur de liens pour ajouter un symbole spécifié à la table de symboles.

Pour spécifier plusieurs symboles, tapez une virgule (,), un point-virgule ( ;) ou un espace entre les noms de symboles. Sur la ligne de commande, spécifiez/INCLUDE :`symbol` une fois pour chaque symbole.

L’éditeur de liens résout `symbol` en ajoutant l’objet qui contient la définition du symbole au programme. Cette fonctionnalité est utile pour inclure un objet de bibliothèque qui ne serait sinon pas lié au programme.

Spécification d’un symbole avec cette option substitue à la suppression de ce symbole par [/OPT : REF](opt-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **entrée** page de propriétés.

1. Modifier le **références des symboles forcées** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
