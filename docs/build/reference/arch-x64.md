---
description: En savoir plus sur les éléments suivants:/Arch (x64)
title: /arch (x64)
ms.date: 10/01/2019
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: 1e9670cdea49c06eda6575fe2cea872072a4e332
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183072"
---
# <a name="arch-x64"></a>/arch (x64)

Spécifie l'architecture pour la génération de code sur x64. Consultez également [/Arch (x86)](arch-x86.md) et [/Arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[AVX|AVX2|AVX512]
```

## <a name="arguments"></a>Arguments

**/Arch : AVX**<br/>
Active l'utilisation des instructions Intel Advanced Vector Extensions.

**/Arch : AVX2**<br/>
Active l’utilisation des instructions Intel Advanced Vector Extensions 2.

**/Arch : AVX512**<br/>
Active l’utilisation des instructions Intel Advanced Vector Extensions 512.

## <a name="remarks"></a>Notes

L’option **/ARCH** permet l’utilisation de certaines extensions de jeu d’instructions, en particulier pour le calcul de vecteurs, disponibles dans les processeurs d’Intel et AMD. En général, les processeurs plus récemment introduits peuvent prendre en charge des extensions supplémentaires par rapport à celles prises en charge par les anciens processeurs, même si vous devez consulter la documentation d’un processeur particulier ou tester la prise en charge de l’extension de jeu d’instructions à l’aide de [__cpuid](../../intrinsics/cpuid-cpuidex.md) avant d’exécuter du code avec une extension de jeu d’instructions.

**/ARCH** affecte uniquement la génération de code pour les fonctions natives. Quand vous utilisez [/CLR](clr-common-language-runtime-compilation.md) pour compiler, **/ARCH** n’a aucun effet sur la génération de code pour les fonctions managées.

Les extensions du processeur présentent les caractéristiques suivantes :

- Le mode par défaut utilise des instructions SSE2 pour les calculs à virgule flottante scalaire et les calculs de vecteur. Ces instructions permettent le calcul avec des vecteurs 128 bits de valeurs entières à simple précision, à double précision et à 1, 2, 4 ou 8 octets, ainsi que des valeurs à virgule flottante scalaires à simple précision et à double précision.

- **AVX** a introduit un autre encodage d’instruction pour les instructions scalaires vectorielles et à virgule flottante qui autorisent les vecteurs de 128 bits ou 256 bits, et qui étend tous les résultats de vecteurs à la taille vectorielle complète. (Pour la compatibilité héritée, les instructions de Vector de style SSE préservent tous les bits au-delà du bit 127.) La plupart des opérations à virgule flottante sont étendues à 256 bits.

- **AVX2** étend la plupart des opérations d’entiers aux vecteurs 256 bits et permet l’utilisation d’instructions Multiply-Addes fusionnées (FMA).

- **AVX-512** a introduit un autre formulaire d’encodage d’instruction qui autorise les vecteurs 512 bits, ainsi que certaines autres fonctionnalités facultatives. Des instructions relatives à des opérations supplémentaires ont également été ajoutées.

Chaque option **/ARCH** peut également permettre l’utilisation d’autres instructions non vectorielles associées à cette option. Un exemple est l’utilisation de certaines instructions IMC quand **/arch : AVX2** est spécifié.

Le `__AVX__` symbole de préprocesseur est défini quand l’option de compilateur **/arch : AVX**, **/arch : AVX2** ou **/arch : AVX512** est spécifiée. Le `__AVX2__` symbole de préprocesseur est défini quand l’option de compilateur **/arch : AVX2** ou **/arch : AVX512** est spécifiée. Les `__AVX512F__` `__AVX512CD__` symboles de `__AVX512BW__` préprocesseur,, `__AVX512DQ__` et `__AVX512VL__` sont définis lorsque l’option de compilateur **/arch : AVX512** est spécifiée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md). L’option **/arch : AVX2** a été introduite dans Visual Studio 2013 Update 2, version 12.0.34567.1. Prise en charge limitée de **/arch : AVX512** a été ajoutée dans visual studio 2017 et développée dans visual studio 2019.

### <a name="to-set-the-archavx-archavx2-or-archavx512-compiler-option-in-visual-studio"></a>Pour définir l’option de compilateur/arch : AVX,/Arch : AVX2 ou/arch : AVX512 dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **Propriétés de configuration**, **C/C++** .

1. Sélectionnez la page de propriétés **génération de code** .

1. Dans la zone de liste déroulante **activer le jeu d’instructions amélioré** , choisissez **Advanced Vector Extensions (/Arch : AVX)** et **Advanced Vector Extensions 2 (/Arch : AVX2)** ou **Advanced Vector Extensions 512 (/Arch : AVX512)**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Voir aussi

[/Arch (architecture d’UC minimale)](arch-minimum-cpu-architecture.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
