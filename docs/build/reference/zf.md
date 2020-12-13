---
description: En savoir plus sur:/ZF (génération de fichier PDB plus rapide)
title: /Zf (Génération PDB plus rapide)
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: 6acf84de3c286131f470808505cdf0e895feeaeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178886"
---
# <a name="zf-faster-pdb-generation"></a>/Zf (Génération PDB plus rapide)

Activez la génération PDB plus rapide dans les builds parallèles en minimisant les appels RPC à mspdbsrv.exe.

## <a name="syntax"></a>Syntaxe

> **/ZF**

## <a name="remarks"></a>Notes

L’option **/ZF** permet la prise en charge du compilateur pour une génération plus rapide de fichiers PDB lors de l’utilisation de l’option [/MP (générer avec plusieurs processus)](mp-build-with-multiple-processes.md) ou lorsque le système de génération (par exemple, [MSBuild](/visualstudio/msbuild/msbuild-reference) ou [cmake](../cmake-projects-in-visual-studio.md)) peut exécuter plusieurs processus de compilation cl.exe en même temps. Avec cette option, le compilateur frontal retarde la génération d’index de type pour chaque enregistrement de type dans le fichier PDB jusqu’à la fin de la compilation, puis les demande dans un seul appel RPC à mspdbsrv.exe, au lieu d’effectuer une demande RPC pour chaque enregistrement. Cela peut améliorer considérablement le débit de la génération en réduisant la charge RPC sur le processus de mspdbsrv.exe dans un environnement où plusieurs processus de compilation de cl.exe s’exécutent simultanément.

Étant donné que l’option **/ZF** s’applique uniquement à la génération PDB, elle nécessite l’option [/Zi](z7-zi-zi-debug-information-format.md) ou [/Zi](z7-zi-zi-debug-information-format.md) .

L’option **/ZF** est disponible à partir de Visual Studio 2017 version 15,1, où elle est désactivée par défaut. À compter de Visual Studio 2017 version 15,7 Preview 3, cette option est activée par défaut lorsque l’option **/Zi** ou **/Zi** est activée.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **options supplémentaires** pour inclure **/ZF** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur classées par ordre alphabétique](compiler-options-listed-alphabetically.md)<br/>
[/MP (générer avec plusieurs processus)](mp-build-with-multiple-processes.md)<br/>
