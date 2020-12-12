---
description: En savoir plus sur les éléments suivants:/Arch (x86)
title: /arch (x86)
ms.date: 10/01/2019
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: a37f0b5cfe1907108bdd5fb71de774a84f585676
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183059"
---
# <a name="arch-x86"></a>/arch (x86)

Spécifie l'architecture pour la génération de code sur x86. Consultez également [/Arch (x64)](arch-x64.md) et [/Arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[IA32|SSE|SSE2|AVX|AVX2|AVX512]
```

## <a name="arguments"></a>Arguments

**/Arch : IA32**<br/>
Ne spécifie aucune instruction améliorée et spécifie x87 pour les calculs à virgule flottante.

**/Arch : SSE**<br/>
Permet l'utilisation d'instructions SSE.

**/Arch : SSE2**<br/>
Permet l'utilisation d'instructions SSE2. Il s’agit de l’instruction par défaut sur les plateformes x86 si aucune option **/ARCH** n’est spécifiée.

**/Arch : AVX**<br/>
Active l'utilisation des instructions Intel Advanced Vector Extensions.

**/Arch : AVX2**<br/>
Active l’utilisation des instructions Intel Advanced Vector Extensions 2.

**/Arch : AVX512**<br/>
Active l’utilisation des instructions Intel Advanced Vector Extensions 512.

## <a name="remarks"></a>Notes

L’option **/ARCH** active ou désactive l’utilisation de certaines extensions de jeu d’instructions, en particulier pour le calcul de vecteurs, disponibles dans les processeurs d’Intel et AMD. En général, les processeurs plus récemment introduits peuvent prendre en charge des extensions supplémentaires par rapport à celles prises en charge par les anciens processeurs, même si vous devez consulter la documentation d’un processeur particulier ou tester la prise en charge de l’extension de jeu d’instructions à l’aide de [__cpuid](../../intrinsics/cpuid-cpuidex.md) avant d’exécuter du code avec une extension de jeu d’instructions.

**/ARCH** affecte uniquement la génération de code pour les fonctions natives. Quand vous utilisez [/CLR](clr-common-language-runtime-compilation.md) pour compiler, **/ARCH** n’a aucun effet sur la génération de code pour les fonctions managées.

Les options **/ARCH** font référence aux extensions de jeu d’instructions avec les caractéristiques suivantes :

- **Ia32** est le jeu d’instructions x86 32 bits hérité sans opérations vectorielles et utilisant X87 pour les calculs à virgule flottante.

- **SSE** autorise le calcul avec des vecteurs de quatre valeurs à virgule flottante simple précision. Les instructions de virgule flottante scalaires correspondantes ont également été ajoutées.

- **SSE2** permet le calcul avec des vecteurs 128 bits de valeurs entières à simple précision, à double précision et à 1, 2, 4 ou 8 octets. Des instructions scalaires à double précision ont également été ajoutées.

- **AVX** a introduit un autre encodage d’instruction pour les instructions scalaires vectorielles et à virgule flottante qui autorisent les vecteurs de 128 bits ou 256 bits, et qui étend tous les résultats de vecteurs à la taille vectorielle complète. (Pour la compatibilité héritée, les instructions de Vector de style SSE préservent tous les bits au-delà du bit 127.) La plupart des opérations à virgule flottante sont étendues à 256 bits.

- **AVX2** étend la plupart des opérations d’entiers aux vecteurs 256 bits et permet l’utilisation d’instructions Multiply-Addes fusionnées (FMA).

- **AVX512** a introduit un autre formulaire d’encodage d’instruction qui autorise les vecteurs 512 bits, ainsi que certaines autres fonctionnalités facultatives. Des instructions relatives à des opérations supplémentaires ont également été ajoutées.

L’optimiseur choisit quand et comment utiliser les instructions vectorielles en fonction du **/ARCH** spécifié. Les calculs scalaires à virgule flottante sont effectués avec des instructions SSE ou AVX lorsqu’elles sont disponibles. Certaines conventions d’appel spécifient le passage d’arguments à virgule flottante sur la pile X87 et, par conséquent, votre code peut utiliser une combinaison d’instructions X87 et SSE/AVX pour les calculs à virgule flottante. Les instructions de vecteur entier peuvent également être utilisées pour des opérations d’entiers 64 bits quand elles sont disponibles.

Outre les instructions scalaires vectorielles et à virgule flottante, chaque option **/ARCH** peut également permettre l’utilisation d’autres instructions non vectorielles associées à cette option. Par exemple, la famille d’instructions CMOVcc apparaissant pour la première fois sur les processeurs Intel Pentium Pro. Étant donné que les instructions SSE ont été introduites avec le processeur Intel Pentium III suivant, des instructions CMOVcc peuvent être générées, sauf si **/arch : ia32** est spécifié.

Les opérations en virgule flottante sont normalement arrondies à la double précision (64 bits) dans le code X87, mais vous pouvez utiliser `_controlfp` pour modifier le mot de contrôle FP, y compris définir le contrôle de précision sur la précision étendue (80 bits) ou la précision simple (32 bits). Pour plus d’informations, consultez [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). SSE et AVX comportent des instructions séparées à simple précision et à double précision pour chaque opération, donc il n’y a pas d’équivalent pour le code SSE/AVX. Cela peut modifier la manière dont les résultats sont arrondis lorsque le résultat d’une opération à virgule flottante est utilisé directement dans le calcul supplémentaire au lieu de l’assigner à une variable utilisateur. Tenez compte des éléments suivants :

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

Avec attribution explicite :

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

**/ARCH** et [/QIfist](qifist-suppress-ftol.md) ne peuvent pas être utilisés sur le même compiland. L’option **/QIfist** modifie le comportement d’arrondi de la virgule flottante en conversion d’entier. Le comportement par défaut consiste à tronquer (arrondi vers zéro), tandis que l’option **/QIfist** spécifie l’utilisation du mode d’arrondi de l’environnement à virgule flottante. Comme cela modifie le comportement de toutes les conversions à virgule flottante en nombres entiers, cet indicateur est déconseillé. Lors de la compilation pour SSE ou AVX, vous pouvez arrondir une valeur à virgule flottante à un entier à l’aide du mode d’arrondi de l’environnement à virgule flottante à l’aide d’une séquence de fonctions intrinsèques :

```cpp
int convert_float_to_int(float x) {
    return _mm_cvtss_si32(_mm_set_ss(x));
}

int convert_double_to_int(double x) {
    return _mm_cvtsd_si32(_mm_set_sd(x));
}
```

Les `_M_IX86_FP` `__AVX__` `__AVX2__` macros,,,,, `__AVX512F__` `__AVX512CD__` `__AVX512BW__` `__AVX512DQ__` et indiquent l' `__AVX512VL__` option du compilateur **/ARCH** (le cas échéant) qui a été utilisée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md). L’option **/arch : AVX2** et la `__AVX2__` macro ont été introduites dans Visual Studio 2013 Update 2, version 12.0.34567.1. Prise en charge limitée de **/arch : AVX512** a été ajoutée dans visual studio 2017 et développée dans visual studio 2019.

### <a name="to-set-this-compiler-option-for-avx-avx2-avx512-ia32-sse-or-sse2-in-visual-studio"></a>Pour définir cette option de compilateur pour AVX, AVX2, AVX512, IA32, SSE ou SSE2 dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **Propriétés de configuration**, **C/C++** .

1. Sélectionnez la page de propriétés **génération de code** .

1. Modifiez la propriété **activer le jeu d’instructions amélioré** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Voir aussi

[/Arch (architecture d’UC minimale)](arch-minimum-cpu-architecture.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
