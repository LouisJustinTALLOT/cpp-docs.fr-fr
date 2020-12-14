---
description: En savoir plus sur les éléments suivants:/VMB,/vmg (méthode de représentation)
title: /vmb, /vmg (Méthode de représentation)
ms.date: 11/04/2016
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
ms.openlocfilehash: 19d183ef8d1dd152043d7249d907c9d5b48de230
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254280"
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg (Méthode de représentation)

Sélectionnez la méthode que le compilateur utilise pour représenter des pointeurs vers des membres de classe.

Utilisez **/VMB** si vous définissez toujours une classe avant de déclarer un pointeur vers un membre de la classe.

Utilisez **/VMG** pour déclarer un pointeur vers un membre d’une classe avant de définir la classe. Ce besoin peut survenir si vous définissez des membres dans deux classes différentes qui se référencent mutuellement. Pour les classes qui référencent mutuellement, une classe doit être référencée avant d’être définie.

## <a name="syntax"></a>Syntaxe

```
/vmb
/vmg
```

## <a name="remarks"></a>Notes

Vous pouvez également utiliser des [Mots clés](../../cpp/inheritance-keywords.md) [Pointers_to_members](../../preprocessor/pointers-to-members.md) ou d’héritage dans votre code pour spécifier une représentation de pointeur.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
