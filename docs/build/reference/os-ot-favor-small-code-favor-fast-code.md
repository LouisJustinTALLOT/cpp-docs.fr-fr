---
title: /Os, /Ot (Favoriser la taille du code, Favoriser la vitesse du code)
description: Les options de compilateur MSVC/OS et/OT spécifient s’il faut privilégier la taille ou la vitesse lors de l’optimisation du code.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
ms.openlocfilehash: 384019ddf7b80b8dd4e00197d73d1e4ac536634c
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180823"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>`/Os`, `/Ot` (Favoriser la taille du code, favoriser la vitesse du code)

Réduit ou agrandit la taille des fichiers exe et des dll.

## <a name="syntax"></a>Syntaxe

> **`/Os`**\
> **`/Ot`**

## <a name="remarks"></a>Notes

**`/Os`**(Favoriser le petit code) réduit la taille des fichiers exe et des dll en demandant au compilateur de privilégier la taille sur la vitesse. Le compilateur peut réduire de nombreuses constructions C et C++ pour des séquences de code machine fonctionnellement similaires. Parfois, ces différences offrent des compromis entre la taille et la vitesse. Les **`/Os`** **`/Ot`** options et vous permettent de spécifier une préférence pour l’une par rapport à l’autre :

**`/Ot`**(Favoriser la rapidité du code) maximise la vitesse des fichiers exe et des dll en demandant au compilateur de privilégier la vitesse par rapport à la taille. **`/Ot`** est la valeur par défaut lorsque les optimisations sont activées. Le compilateur peut réduire de nombreuses constructions C et C++ pour des séquences de code machine fonctionnellement similaires. Parfois, ces différences offrent des compromis entre la taille et la vitesse. L' **`/Ot`** option est implicite par l' [`/O2`](o1-o2-minimize-size-maximize-speed.md) option (maximiser la vitesse). L' **`/O2`** option combine plusieurs options pour produire du code plus rapide.

> [!NOTE]
> Les informations collectées à partir des séries de tests de profilage remplacent les optimisations qui autrement seraient en vigueur si vous spécifiez **`/Ob`** , **`/Os`** ou **`/Ot`** . Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md).

### <a name="x86-specific-example"></a>exemple spécifique à x86

L’exemple de code suivant illustre la différence entre l' **`/Os`** option (favoriser la taille du code) et l' **`/Ot`** option (favoriser la vitesse du code) :

> [!NOTE]
> Cet exemple décrit le comportement attendu lors de l’utilisation **`/Os`** de ou de **`/Ot`** . Toutefois, le comportement du compilateur de la version Release à la version finale peut entraîner des optimisations différentes pour le code ci-dessous.

```c
/* differ.c
  This program implements a multiplication operator
  Compile with /Os to implement multiply explicitly as multiply.
  Compile with /Ot to implement as a series of shift and LEA instructions.
*/
int differ(int x)
{
    return x * 71;
}
```

Comme indiqué dans le fragment de code machine ci-dessous, quand *`differ.c`* est compilé pour Size ( **`/Os`** ), le compilateur implémente l’expression de multiplication dans l’instruction return explicitement comme une multiplication pour produire une séquence de code brève, mais plus lente :

```asm
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

En guise d’alternative, lorsque *`differ.c`* est compilé pour la vitesse ( **`/Ot`** ), le compilateur implémente l’expression de multiplication dans l’instruction return sous la forme d’une série d’instructions Shift et d' `LEA` instructions pour produire une séquence de code rapide, mais plus longue :

```asm
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation des **Propriétés de configuration**  >  **C/C++**  >  **Optimization** .

1. Modifiez la propriété **favoriser la taille ou la vitesse** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Voir aussi

[/O (Optimiser le code), options](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
