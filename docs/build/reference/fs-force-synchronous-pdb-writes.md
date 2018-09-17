---
title: -FS (forcer les écritures PDB synchrones) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FS
dev_langs:
- C++
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b332782cb9bcd929bcd67d4d81b7a7d0259f53cc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714595"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (forcer les écritures PDB synchrones)

Force est écrit dans le fichier du programme (PDB) de la base de données, créé par [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) ou [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)— à sérialiser via MSPDBSRV. EXE.

## <a name="syntax"></a>Syntaxe

```
/FS
```

## <a name="remarks"></a>Notes

Par défaut, lorsque **/Zi** ou **/Zi** est spécifié, le compilateur verrouille les fichiers PDB pour écrire des informations de type et les informations de débogage symboliques. Cela peut réduire considérablement le temps nécessaire au compilateur de générer des informations de type lorsque le nombre de types est élevé. Si un autre processus verrouille temporairement le fichier PDB — par exemple, un antivirus : écritures par le compilateur peuvent échouer et une erreur irrécupérable peut se produire. Ce problème peut également se produire lorsque le fichier PDB même d’accéder à plusieurs copies de cl.exe, par exemple, si votre solution a indépendants projets qui utilisent la même intermédiaire des répertoires ou les répertoires de sortie et des builds parallèles sont activés. Le **/FS** option du compilateur empêche le compilateur de verrouiller le fichier PDB et force les parcourir MSPDBSRV. EXE, qui sérialise l’accès. Cela risque de rendre les builds beaucoup plus de temps, et il n’empêche pas toutes les erreurs qui peuvent se produire lorsque plusieurs instances de cl.exe d’accès du fichier PDB en même temps. Nous vous recommandons de modifier votre solution afin que les projets indépendants écrire séparer les intermédiaires et emplacements de sortie, ou que vous apportez l’une des projets dépend de l’autre aux générations de projet force sérialisé.

Le [/MP](../../build/reference/mp-build-with-multiple-processes.md) option active **/FS** par défaut.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure `/FS` , puis **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)