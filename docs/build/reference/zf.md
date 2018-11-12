---
title: /ZF (génération PDB plus rapide)
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: 2c3f8d08f59c3a6803eda67126ef8a8f9ba6b1fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595731"
---
# <a name="zf-faster-pdb-generation"></a>/ZF (génération PDB plus rapide)

Activer la génération de PDB plus rapide dans les builds parallèles en réduisant les appels RPC à mspdbsrv.exe.

## <a name="syntax"></a>Syntaxe

> **/Zf**

## <a name="remarks"></a>Notes

Le **/Zf** option permet la prise en charge du compilateur pour la génération plus rapide des fichiers PDB lorsque vous utilisez le [/MP (générer avec plusieurs processus)](mp-build-with-multiple-processes.md) option, ou lorsque le système de génération (par exemple, [MSBuild ](/visualstudio/msbuild/msbuild-reference) ou [CMake](../../ide/cmake-tools-for-visual-cpp.md)) peuvent s’exécuter cl.exe plusieurs processus du compilateur en même temps. Cette option provoque le serveur frontal du compilateur différer la génération d’index de type pour chaque enregistrement de type dans le fichier PDB jusqu'à la fin de la compilation, puis les demande toutes dans un seul appel RPC à mspdbsrv.exe, au lieu de faire une demande RPC pour chaque enregistrement. Cela peut considérablement améliorer le débit de la build en réduisant la charge RPC sur le processus de mspdbsrv.exe dans un environnement où plusieurs processus du compilateur cl.exe s’exécuter simultanément.

Étant donné que le **/Zf** option s’applique uniquement à la génération de PDB, il nécessite le [/Zi](z7-zi-zi-debug-information-format.md) ou [/Zi](z7-zi-zi-debug-information-format.md) option.

Le **/Zf** option est disponible à compter de Visual Studio 2017 version 15.1, où elle est désactivée par défaut. À compter de Visual Studio 2017 version 15.7 Preview 3, cette option est activée par défaut lorsque le **/Zi** ou **/Zi** est activée.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zf** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur classées par ordre alphabétique](compiler-options-listed-alphabetically.md)<br/>
[/MP (Générer avec plusieurs processus)](mp-build-with-multiple-processes.md)<br/>
