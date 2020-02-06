---
title: /Qspectre-load
description: Décrit l’option Microsoft CC++ /compiler (MSVC)/Qspectre-Load.
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load
ms.openlocfilehash: a766cf9b7eef11b7c5819cbdaa7706ab5b80c608
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035528"
---
# <a name="qspectre-load"></a>/Qspectre-load

Spécifie la génération par le compilateur des instructions de sérialisation pour chaque instruction de chargement. Cette option étend l’indicateur **/Qspectre** , ce qui permet d’atténuer les **attaques par canal latéral d’exécution spéculative** possible en fonction des charges.

## <a name="syntax"></a>Syntaxe

> **/Qspectre-load**

## <a name="remarks"></a>Notes

**/Qspectre-Load** fait en sorte que le compilateur détecte les chargements à partir de la mémoire et insère des instructions de sérialisation après celles-ci. Les instructions de workflow de contrôle qui chargent de la mémoire, y compris les `RET` et les `CALL`, sont divisées en une charge et un transfert de Workflow. La charge est suivie d’un `LFENCE` pour garantir la protection de la charge. Dans certains cas, le compilateur ne peut pas fractionner les instructions de contrôle de workflow, telles que l’instruction `jmp`, de sorte qu’il utilise une autre technique d’atténuation. Par exemple, le compilateur atténue `jmp [rax]` en ajoutant des instructions pour charger la cible de manière non destructrice avant d’insérer un LFENCE, comme illustré ici :

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

Comme **/Qspectre-Load** arrête la spéculation de toutes les charges, l’impact sur les performances est élevé. L’atténuation n’est pas appropriée partout. Si des blocs de code critiques pour les performances ne nécessitent pas de protection, vous pouvez désactiver ces atténuations à l’aide de `__declspec(spectre(nomitigation))`. Pour plus d’informations, consultez [__declspec spectre](../../cpp/spectre.md).

L’option **/Qspectre-Load** est désactivée par défaut et prend en charge tous les niveaux d’optimisation.

L’option **/Qspectre-Load** est disponible dans Visual Studio 2019 version 16,5 et versions ultérieures. Cette option est disponible uniquement dans les compilateurs qui ciblent des processeurs x86 et x64. Elle n’est pas disponible dans les compilateurs qui ciblent des processeurs ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

2. Sélectionnez les **Propriétés de configuration** > page de propriétés de **génération de code** **C/C++**  > .

3. Sélectionnez une nouvelle valeur pour la propriété d' **atténuation spectre** . Choisissez **OK** pour appliquer le changement.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)\
[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
