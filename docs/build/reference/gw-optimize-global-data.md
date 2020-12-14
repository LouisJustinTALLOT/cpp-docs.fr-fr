---
description: En savoir plus sur:/GW (optimiser les données globales)
title: /Gw (optimiser les données globales)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 2f9a6b9452f09473e650a5453ad2600cc73f0c00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200141"
---
# <a name="gw-optimize-global-data"></a>/Gw (optimiser les données globales)

Empaquetez les données globales dans les sections COMDAT pour l’optimisation.

## <a name="syntax"></a>Syntaxe

```
/Gw[-]
```

## <a name="remarks"></a>Notes

L’option **/GW** force le compilateur à empaqueter des données globales dans des sections COMDAT individuelles. Par défaut, **/GW** est désactivé et doit être activé explicitement. Pour le désactiver explicitement, utilisez **/GW-**. Quand **/GW** et [/GL](gl-whole-program-optimization.md) sont tous deux activés, l’éditeur de liens utilise l’optimisation de l’ensemble du programme pour comparer des sections COMDAT entre plusieurs fichiers objets afin d’exclure les données globales non référencées ou de fusionner des données globales en lecture seule identiques. Cela peut réduire considérablement la taille de l’exécutable binaire résultant.

Quand vous compilez et liez séparément, vous pouvez utiliser l’option de l’éditeur de liens [/OPT : Ref](opt-optimizations.md) pour exclure de l’exécutable les données globales non référencées dans les fichiers objets compilés avec l’option **/GW** .

Vous pouvez également utiliser les options de l’éditeur de liens [/OPT : ICF](opt-optimizations.md) et [/LTCG](ltcg-link-time-code-generation.md) pour fusionner dans l’exécutable toutes les données globales en lecture seule identiques dans plusieurs fichiers objets compilés avec l’option **/GW** .

Pour plus d’informations, consultez [Introducing/GW compiler Switch](https://devblogs.microsoft.com/cppblog/introducing-gw-compiler-switch/) sur le blog de l’équipe C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **C/C++** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Modifiez la propriété **options supplémentaires** pour inclure **/GW** , puis choisissez **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
