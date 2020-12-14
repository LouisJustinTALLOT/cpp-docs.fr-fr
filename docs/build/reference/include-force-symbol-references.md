---
description: En savoir plus sur:/INCLUDE (forcer les références de symboles)
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
ms.openlocfilehash: 4938f5e92f91718f522df103303e6382005d463c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191301"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Forcer les références des symboles)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>Paramètres

*symbole*<br/>
Spécifie un symbole à ajouter à la table de symboles.

## <a name="remarks"></a>Notes

L’option/INCLUDE indique à l’éditeur de liens d’ajouter un symbole spécifié à la table de symboles.

Pour spécifier plusieurs symboles, tapez une virgule (,), un point-virgule (;) ou un espace entre les noms de symboles. Sur la ligne de commande, spécifiez/INCLUDE : `symbol` once pour chaque symbole.

L’éditeur de liens résout `symbol` en ajoutant l’objet qui contient la définition du symbole au programme. Cette fonctionnalité est utile pour inclure un objet de bibliothèque qui, autrement, ne serait pas lié au programme.

La spécification d’un symbole avec cette option remplace la suppression de ce symbole par [/OPT : Ref](opt-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **entrée** .

1. Modifiez la propriété **forcer les références de symboles** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
