---
description: En savoir plus sur:/Diagnostics (options de diagnostic du compilateur)
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
ms.openlocfilehash: 2c34edc0374e59720eb05e97379702833efaa703
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201415"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/Diagnostics (options de diagnostic du compilateur)

Utilisez l’option du compilateur **/Diagnostics** pour spécifier l’affichage des informations sur l’emplacement des erreurs et des avertissements.

## <a name="syntax"></a>Syntaxe

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>Notes

Cette option est prise en charge dans Visual Studio 2017 et versions ultérieures.

L’option du compilateur **/Diagnostics** contrôle l’affichage des informations d’erreur et d’avertissement.

L’option **/Diagnostics : Classic** est la valeur par défaut, qui indique uniquement le numéro de ligne où le problème a été trouvé.

L’option **/Diagnostics : column** comprend également la colonne dans laquelle le problème a été trouvé. Cela peut vous aider à identifier la construction ou le caractère spécifique du langage qui est à l’origine du problème.

L’option **/Diagnostics : caret** comprend la colonne dans laquelle le problème a été trouvé et place le signe insertion (^) sous l’emplacement dans la ligne de code où le problème a été détecté.

Notez que dans certains cas, le compilateur ne détecte pas un problème où il s’est produit. Par exemple, un point-virgule manquant peut ne pas être détecté tant que d’autres symboles inattendus n’ont pas été détectés. La colonne est signalée et le point d’insertion est placé là où le compilateur a détecté une erreur, ce qui n’est pas toujours là où vous devez effectuer votre correction.

L’option **/Diagnostics** est disponible à partir de Visual Studio 2017.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** de votre projet.

1. Sous **Propriétés de configuration**, développez le dossier **C/C++** , puis choisissez la page de propriétés **général** .

1. Utilisez le contrôle dropdown du champ **format de diagnostics** pour sélectionner une option d’affichage des Diagnostics. Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
