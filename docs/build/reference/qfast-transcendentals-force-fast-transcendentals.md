---
description: En savoir plus sur les éléments suivants:/Qfast_transcendentals (Force Fast fonctions transcendantes rapides)
title: /Qfast_transcendentals (Force Fast Transcendentals)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 7701925aa7df33107b0829ade1c0c711eda14c08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225659"
---
# <a name="qfast_transcendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Force Fast Transcendentals)

Génère du code incorporé pour les fonctions transcendant.

## <a name="syntax"></a>Syntaxe

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Notes

Cette option de compilateur force les fonctions transcendant à être converties en code inline pour améliorer la vitesse d’exécution. Cette option n’a d’effet que lorsqu’elle est associée à **/FP : except** ou **/FP : precise**. La génération de code inline pour les fonctions transcendant est déjà le comportement par défaut sous **/FP : Fast**.

Cette option est incompatible avec **/FP : strict**. Pour plus d’informations sur les options du compilateur à virgule flottante [, consultez/FP (spécifier le comportement de Floating-Point)](fp-specify-floating-point-behavior.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
