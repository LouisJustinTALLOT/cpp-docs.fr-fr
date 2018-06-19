---
title: /ZF (génération plus rapide PDB) | Documents Microsoft
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zf
dev_langs:
- C++
helpviewer_keywords:
- /Zf
- -Zf
author: corob-msft
ms.author: corob
ms.openlocfilehash: 968ce17302fa608888c7ae2fedf695946b0119bd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379963"
---
# <a name="zf-faster-pdb-generation"></a>/ZF (génération PDB plus rapide)

Activer la génération PDB plus rapide dans les builds parallèles en réduisant les appels RPC à mspdbsrv.exe.

## <a name="syntax"></a>Syntaxe

> **/Zf**

## <a name="remarks"></a>Notes

Le **/Zf** option active la prise en charge du compilateur pour la génération plus rapide des fichiers PDB lorsque vous utilisez la [/MP (générer avec plusieurs processus)](mp-build-with-multiple-processes.md) option, ou lorsque le système de génération (par exemple, [MSBuild ](/visualstudio/msbuild/msbuild-reference) ou [CMake](../../ide/cmake-tools-for-visual-cpp.md)) peuvent s’exécuter cl.exe plusieurs processus du compilateur en même temps. Cette option entraîne le compilateur frontal différer la génération de l’index de type pour chaque enregistrement de type dans le fichier PDB jusqu'à la fin de la compilation, puis les demande tous dans un seul appel RPC mspdbsrv.exe, au lieu d’effectuer une demande RPC pour chaque enregistrement. Cela peut considérablement améliorer le débit de la build en réduisant la charge RPC sur le processus de mspdbsrv.exe dans un environnement où plusieurs processus du compilateur cl.exe s’exécutent simultanément.

Étant donné que la **/Zf** option s’applique uniquement à la génération du fichier PDB, il requiert le [/Zi](z7-zi-zi-debug-information-format.md) ou [/Zi](z7-zi-zi-debug-information-format.md) option.

Le **/Zf** option est disponible à compter de Visual Studio 2017 version 15,1, où elle est désactivée par défaut. À compter de Visual Studio 2017 version 15.7 Preview 3, cette option est activée par défaut lorsque le **/Zi** ou **/Zi** est activée.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier la **des Options supplémentaires** propriété à inclure **/Zf** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur classées par ordre alphabétique](compiler-options-listed-alphabetically.md)<br/>
[/MP (Générer avec plusieurs processus)](mp-build-with-multiple-processes.md)<br/>
