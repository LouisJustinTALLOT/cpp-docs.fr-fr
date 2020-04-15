---
title: /Os, /Ot (Favoriser la taille du code, Favoriser la vitesse du code)
ms.date: 11/04/2016
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
ms.openlocfilehash: 0eda9461b3ef730e0e0a832aa94a688e03c7e1bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336189"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Favoriser la taille du code, Favoriser la vitesse du code)

Minimise ou maximise la taille des EXE et des DLL.

## <a name="syntax"></a>Syntaxe

```
/Os
/Ot
```

## <a name="remarks"></a>Notes

**/Os** (Favor Small Code) minimise la taille des EXE et des DLL en instruisant le compilateur de privilégier la taille à la vitesse. Le compilateur peut réduire de nombreuses constructions C et C à des séquences fonctionnellement similaires de code machine. Parfois, ces différences offrent des compromis de taille par rapport à la vitesse. Les options **/Os** et **/Ot** vous permettent de spécifier une préférence pour l’un plutôt que pour l’autre :

**/Ot** (Favor Fast Code) maximise la vitesse des EXE et des DLL en instruisant le compilateur de favoriser la vitesse sur la taille. (C’est la valeur par défaut.) Le compilateur peut réduire de nombreuses constructions C et C à des séquences fonctionnellement similaires de code machine. De temps en temps, ces différences offrent des compromis de taille par rapport à la vitesse. **L’option /Ot** est implicite par l’option Vitesse Maxim ([/O2).](o1-o2-minimize-size-maximize-speed.md) **L’option /O2** combine plusieurs options pour produire du code très rapide.

Si vous utilisez **/Os** ou **/Ot**, alors vous devez également spécifier [/Og](og-global-optimizations.md) pour optimiser le code.

> [!NOTE]
> Les informations recueillies à partir des essais de profilage remplaceront les optimisations qui seraient autrement en vigueur si vous spécifiez **/Ob**, **/Os**, ou **/Ot**. Pour plus d’informations, [Profile-Guided Optimizations](../profile-guided-optimizations.md).

**Section spécifique à x86**

Le code d’exemple suivant démontre la différence entre les options Favor Small Code (**/Os**) et l’option Code rapide Favor (**/Ot)**:

> [!NOTE]
> Ce qui suit décrit le comportement attendu lors de l’utilisation **/Os** ou **/Ot**. Cependant, le comportement compilateur de la libération à la libération peut entraîner des optimisations différentes pour le code ci-dessous.

```
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

Comme le montre le fragment de code de la machine ci-dessous, lorsque DIFFER.c est compilé pour la taille (**/Os**), le compilateur implémente l’expression de multiplication dans la déclaration de retour explicitement comme une multiplication pour produire une séquence courte mais plus lente de code:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Alternativement, lorsque DIFFER.c est compilé pour la vitesse (**/Ot**), le compilateur implémente l’expression de multiplication dans l’énoncé de retour comme une série de décalage et `LEA` d’instructions pour produire une séquence rapide mais plus longue de code:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**END x86 Spécifique**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriété **Optimization.**

1. Modifier la taille de la faveur ou la propriété **Speed.**

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Voir aussi

[/O (Optimiser le code), options](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
