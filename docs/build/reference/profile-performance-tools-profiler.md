---
description: En savoir plus sur:/PROFILE (Performance Tools Profiler)
title: /PROFILE (Profileur des outils d'analyse des performances)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: fb9310bb782a4b321113155f01db2228e3a46e15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225789"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profileur des outils d'analyse des performances)

Génère un fichier de sortie utilisable avec le profileur Outils d’analyse des performances.

## <a name="syntax"></a>Syntaxe

```
/PROFILE
```

## <a name="remarks"></a>Notes

/PROFILE implique les options de l’éditeur de liens suivantes :

- [/OPT : REF](opt-optimizations.md)

- /OPT : NOICF

- [/INCREMENTAL : NON](incremental-link-incrementally.md)

- [/FIXED : NON](fixed-fixed-base-address.md)

/PROFILE force l’éditeur de liens à générer une section de réadressage dans l’image du programme.  Une section de réadressage permet au profileur de transformer l’image de programme pour obtenir des données de profil.

**/Profile** est uniquement disponible dans les versions Enterprise (Team Development).  Pour plus d’informations sur PREfast, consultez [vue d’ensemble de l’analyse du code pour C/C++](../../code-quality/code-analysis-for-c-cpp-overview.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **Éditeur de liens**.

1. Sélectionnez la page de propriétés **Avancé**.

1. Modifiez la propriété de **Profil** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>Pour définir cette option de l’éditeur de liens dans le projet Visual Studio CMake

Le projet **cmake** n’a pas de **page de propriétés**, les options de l’éditeur de liens peuvent être définies en modifiant l' CMakeLists.txt.

1. Ouvrez le CMakeLists.txt dans le répertoire racine du projet.

1. Ajoutez le code ci-dessous. Pour plus d’informations, consultez [références cmake](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. Regénérez votre solution.

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
