---
title: Vue d’ensemble de l’analyse du code C/C++
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
ms.openlocfilehash: e5f5b75057985dc769c8f1ab84765d628dc42fcc
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040300"
---
# <a name="code-analysis-for-cc-overview"></a>Vue d’ensemble de l’analyse du code C/C++

L’outil d’analyse du code C/C++ fournit des informations sur les erreurs possibles dans votre code source C/C++. Les erreurs de codage courantes signalées par l'outil sont notamment les dépassements de mémoire tampon, une mémoire non initialisée, les déréférencements du pointeur Null et les fuites de mémoire et de ressources. L’outil peut également exécuter des vérifications par rapport au [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Intégration de l’IDE (environnement de développement intégré)

L’outil d’analyse du code est entièrement intégré dans l’IDE de Visual Studio.

Durant le processus de génération, tous les avertissements générés pour le code source s’affichent dans la liste d’erreurs. Vous pouvez accéder au code source à l’origine de l’avertissement, et afficher des informations supplémentaires sur la cause et les solutions possibles du problème.

## <a name="command-line-support"></a>Prise en charge de la ligne de commande

Vous pouvez également utiliser l’outil d’analyse à partir de la ligne de commande, comme indiqué dans l’exemple suivant :

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 version 15,7 et versions ultérieures :** Vous pouvez exécuter l’outil à partir de la ligne de commande avec n’importe quel système de génération, y compris CMake.

## <a name="pragma-support"></a>support #pragma

Vous pouvez utiliser la `#pragma` directive pour traiter les avertissements comme des erreurs, activer ou désactiver les avertissements et supprimer les avertissements pour les lignes de code individuelles. Pour plus d’informations, consultez [Directives pragma et mot clé __Pragma](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Prise en charge des annotations

Les annotations améliorent la précision de l’analyse du code. Les annotations fournissent des informations supplémentaires sur les conditions préalables et postérieures des paramètres de fonction et des types de retour. Pour plus d’informations, consultez [utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Exécuter l’outil d’analyse dans le cadre d’une stratégie d’archivage

Vous pouvez être amené à imposer que tous les archivages de code source respectent certaines stratégies. En particulier, vous souhaitez vérifier que l’analyse a été exécutée en tant qu’étape de la build locale la plus récente. Pour plus d’informations sur l’activation d’une stratégie d’archivage de l’analyse du code, consultez [création et utilisation de stratégies d’archivage de l’analyse du code](/visualstudio/code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies).

## <a name="team-build-integration"></a>Intégration Team Build

Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l’outil d’analyse du code en tant qu’étape du processus de génération Azure DevOps. Pour plus d’informations, consultez [Azure Pipelines](/azure/devops/pipelines/index).

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide : analyse du code pour C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Procédure pas à pas : analyse du code C/C++ pour les erreurs](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Analyse du code pour les avertissements C/C++](code-analysis-for-c-cpp-warnings.md)
- [Utiliser les vérificateurs de C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [Référence du vérificateur de C++ Core Guidelines](code-analysis-for-cpp-corecheck.md)
- [Utiliser des ensembles de règles pour spécifier les règles C++ à exécuter](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analyser la qualité du pilote à l’aide des outils d’analyse du code](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Avertissements de l'analyse du code pour les pilotes](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
