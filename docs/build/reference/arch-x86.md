---
title: -arch (x86) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f255c8c178d063c040dca4ed6da52c65370c96b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702662"
---
# <a name="arch-x86"></a>/arch (x86)

Spécifie l'architecture pour la génération de code sur x86. Consultez également [/arch (x64)](../../build/reference/arch-x64.md) et [/arch (ARM)](../../build/reference/arch-arm.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[IA32|SSE|SSE2|AVX|AVX2]
```

## <a name="arguments"></a>Arguments

**/ arch : IA32**<br/>
Ne spécifie aucune instruction améliorée et spécifie x87 pour les calculs à virgule flottante.

**/ arch : SSE**<br/>
Permet l'utilisation d'instructions SSE.

**/ arch : SSE2**<br/>
Permet l'utilisation d'instructions SSE2. Voici l’instruction par défaut sur x86 plateformes si aucun **/arch** option est spécifiée.

**/ arch : AVX**<br/>
Active l’utilisation des instructions Intel Advanced Vector Extensions.

**/ arch : avx2**<br/>
Active l’utilisation des instructions Intel Advanced Vector Extensions 2.

## <a name="remarks"></a>Notes

Les instructions SSE et SSE2 existent sur divers processeurs Intel et AMD. Les instructions AVX existe sur les processeurs Intel Sandy Bridge et les processeurs AMD Bulldozer. Les instructions AVX2 sont prises en charge par les processeurs Intel Haswell et Broadwell et les processeurs basés sur AMD Excavator.

Le `_M_IX86_FP`, `__AVX__` et `__AVX2__` macros indiquent ce qui, le cas échéant, **/arch** option du compilateur a été utilisée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md). Le **/arch : avx2** option et `__AVX2__` macro ont été introduites dans Visual Studio 2013 Update 2, version 12.0.34567.1.

L’optimiseur choisit quand et comment utiliser les instructions SSE et SSE2 lorsque **/arch** est spécifié. Il utilise les instructions SSE et SSE2 pour certains calculs scalaires à virgule flottante quand il détermine qu'il est plus rapide d'utiliser les instructions et les registres SSE/SSE2 que la pile de registres à virgule flottante x87. En conséquence, votre code peut en fait utiliser un mélange x87 et SSE/SSE2 pour les calculs à virgule flottante. En outre, avec **/arch : SSE2**, les instructions SSE2 peuvent être utilisées pour certaines opérations sur les entiers de 64 bits.

Outre l'utilisation des instructions SSE et SSE2, le compilateur utilise également d'autres instructions présentes sur les révisions de processeur qui prennent en charge SSE et SSE2. Un exemple de cela est l'instruction CMOV qui est apparue pour la première fois sur la révision Pentium Pro des processeurs Intel.

Étant donné que le x86 compilateur génère du code qui utilise les instructions SSE2 par défaut, vous devez spécifier **/arch : IA32** pour désactiver la génération d’instructions SSE et SSE2 pour x86 processeurs.

**/ arch** uniquement affecte la génération pour les fonctions natives de code. Lorsque vous utilisez [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) à compiler, **/arch** n’a aucun effet sur la génération de code pour les fonctions managées.

**/ arch** et [/QIfist](../../build/reference/qifist-suppress-ftol.md) ne peut pas être utilisé sur le même compiland. En particulier, si vous n'utilisez pas `_controlfp` pour modifier le mot de commande FP, le code de démarrage runtime définit le champ de contrôle de précision de mot de commande FPU x87 sur 53 bits. Par conséquent, chaque opération float ou double d'une expression utilise une mantisse de 53 bits et un exposant de 15 bits. Toutefois, chaque opération simple précision SSE utilise une mantisse de 24 bits et un exposant de 8 bits, tandis que les opérations double précision SSE2 utilisent une mantisse de 53 bits et un exposant de 11 bits. Pour plus d’informations, consultez [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). Ces différences sont possibles dans une même arborescence d’expression, mais pas dans les cas où une affectation d’utilisateurs intervient après chaque sous-expression. Considérez ce qui suit :

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

Comparer :

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>Pour définir cette option de compilateur pour AVX, AVX2, IA32, SSE ou SSE2 dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration**, **C/C++** dossier.

1. Sélectionnez le **génération de Code** page de propriétés.

1. Modifier le **activer du jeu d’instructions amélioré** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Voir aussi

[/arch (Architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md)
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)