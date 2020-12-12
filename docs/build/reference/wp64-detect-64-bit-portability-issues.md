---
description: En savoir plus sur:/Wp64 (détecter les problèmes de portabilité 64 bits)
title: /Wp64 (Détecter les problèmes de portabilité 64 bits)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: d1ee441089531c4ebe222c73f6cec16b59fa7583
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261084"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Détecter les problèmes de portabilité 64 bits)

L'option du compilateur est obsolète. Dans les versions de Visual studio antérieures à Visual Studio 2013, cette option détecte les problèmes de portabilité 64 bits sur les types qui sont également marqués avec le mot clé [__w64](../../cpp/w64.md) .

## <a name="syntax"></a>Syntaxe

```
/Wp64
```

## <a name="remarks"></a>Notes

Par défaut, dans les versions de Visual Studio antérieures à Visual Studio 2013, l’option du compilateur **/Wp64** est désactivée dans le compilateur MSVC qui génère le code x86 32 bits, et dans le compilateur MSVC qui génère le code x64 64 bits.

> [!IMPORTANT]
> L'option de compilateur [/Wp64](wp64-detect-64-bit-portability-issues.md) et le mot clé [__w64](../../cpp/w64.md) sont déconseillés dans Visual Studio 2010 et Visual Studio 2012 et non pris en charge depuis Visual Studio 2013. Si vous convertissez un projet qui utilise ce commutateur, le commutateur ne sera pas migré lors de la conversion. Pour utiliser cette option dans Visual Studio 2010 ou Visual Studio 2012, vous devez taper le commutateur du compilateur sous **Options supplémentaires** dans la section **Ligne de commande** des propriétés du projet. Si vous utilisez l’option de compilateur **/Wp64** sur la ligne de commande, le compilateur émet l’avertissement de ligne de commande D9002. Au lieu d’utiliser cette option et un mot clé pour détecter les problèmes de portabilité 64 bits, utilisez un compilateur MSVC qui cible une plateforme 64 bits et spécifiez l’option [/W4](compiler-option-warning-level.md) . Pour plus d’informations, consultez [configurer des projets C++ pour les cibles 64 bits, x64](../configuring-programs-for-64-bit-visual-cpp.md).

Les variables des types suivants sont testées sur un système d’exploitation 32 bits comme si elles étaient utilisées sur un système d’exploitation 64 bits :

- int

- long

- pointeur

Si vous compilez régulièrement votre application à l’aide d’un compilateur qui génère du code x64 64 bits, vous pouvez simplement désactiver **/Wp64** dans vos compilations 32 bits, car le compilateur 64 bits détectera tous les problèmes. Pour plus d’informations sur la façon de cibler un système d’exploitation Windows 64 bits, consultez [configurer des projets C++ pour les cibles 64 bits et x64](../configuring-programs-for-64-bit-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet.

   Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Changez la zone **Options supplémentaires** pour y inclure **/Wp64**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Configurer des projets C++ pour des cibles x64 64 bits](../configuring-programs-for-64-bit-visual-cpp.md)
