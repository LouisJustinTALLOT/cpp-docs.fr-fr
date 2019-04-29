---
title: /Diagnostics (options de diagnostic du compilateur)
ms.date: 11/11/2016
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6b7d043e00204fa191530f03bbed069d71a25fc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293821"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/Diagnostics (options de diagnostic du compilateur)

Utilisez le **/diagnostics** option du compilateur pour spécifier l’affichage des informations d’emplacement erreur et d’avertissement.

## <a name="syntax"></a>Syntaxe

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>Notes

Cette option est prise en charge dans Visual Studio 2017 et versions ultérieures.

Le **/diagnostics** option du compilateur contrôle l’affichage des informations d’erreur et avertissement.

Le **/diagnostics:classic** option est la valeur par défaut, qui signale uniquement le numéro de ligne où le problème a été trouvé.

Le **/diagnostics:column** option inclut également la colonne où le problème a été trouvé. Cela peut vous aider à identifier la construction de langage spécifique ou un caractère qui provoque le problème.

Le **/diagnostics:caret** option permet d’inclure la colonne où le problème a été trouvé et place le signe insertion (^) sous l’emplacement dans la ligne de code où le problème a été détecté.

Notez que, dans certains cas, le compilateur ne détecte pas un problème où il s’est produite. Par exemple, un point-virgule manquant peuvent ne pas être détecté en tant que symboles autres, inattendues ont été rencontrées. La colonne est signalée et le point d’insertion est placé dans lequel le compilateur a détecté que transmettaient, qui n’est pas toujours où vous avez besoin effectuer votre correction.

Le **/diagnostics** option est disponible à partir de Visual Studio 2017.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez votre projet **Pages de propriétés** boîte de dialogue.

1. Sous **propriétés de Configuration**, développez le **C/C++** dossier et choisissez le **général** page de propriétés.

1. Utiliser le contrôle de liste déroulante dans le **Diagnostics Format** option d’affichage de champ pour sélectionner un diagnostic. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
