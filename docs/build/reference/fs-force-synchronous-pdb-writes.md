---
description: En savoir plus sur:/FS (forcer les écritures PDB synchrones)
title: /FS (forcer les écritures PDB synchrones)
ms.date: 11/04/2016
f1_keywords:
- /FS
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
ms.openlocfilehash: 2dcddd046cc7232f40be5a54d73e659ed099e85d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192029"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (forcer les écritures PDB synchrones)

Force la sérialisation des écritures dans le fichier de base de données du programme (PDB), créé par [/Zi](z7-zi-zi-debug-information-format.md) ou [/zi](z7-zi-zi-debug-information-format.md), via MSPDBSRV.EXE.

## <a name="syntax"></a>Syntaxe

```
/FS
```

## <a name="remarks"></a>Notes

Par défaut, quand **/Zi** ou **/Zi** est spécifié, le compilateur verrouille les fichiers PDB pour écrire des informations de type et des informations de débogage symboliques. Cela peut réduire considérablement le temps nécessaire au compilateur pour générer des informations de type lorsque le nombre de types est élevé. Si un autre processus verrouille temporairement le fichier PDB (par exemple, un programme antivirus), les écritures par le compilateur peuvent échouer et une erreur irrécupérable peut se produire. Ce problème peut également se produire lorsque plusieurs copies de cl.exe accéder au même fichier PDB, par exemple, si votre solution a des projets indépendants qui utilisent les mêmes répertoires intermédiaires ou répertoires de sortie, et si les builds parallèles sont activées. L’option de compilateur **/FS** empêche le compilateur de verrouiller le fichier PDB et force les écritures à passer par MSPDBSRV.EXE, qui sérialise l’accès. Cela peut rendre les builds beaucoup plus longues et n’empêche pas toutes les erreurs qui peuvent se produire lorsque plusieurs instances de cl.exe accéder au fichier PDB en même temps. Nous vous recommandons de modifier votre solution afin que les projets indépendants écrivent dans des emplacements intermédiaires et de sortie, ou que vous rendiez l’un des projets dépendants de l’autre pour forcer la génération de projets sérialisés.

L’option [/MP](mp-build-with-multiple-processes.md) active **/FS** par défaut.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **C/C++** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Modifiez la propriété **options supplémentaires** pour inclure `/FS` , puis cliquez sur **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
