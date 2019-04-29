---
title: /PROFILE (Profileur des outils d'analyse des performances)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 23cbccba9a8ec839252d553cc5cbafd37e66bbf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320199"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profileur des outils d'analyse des performances)

Génère un fichier de sortie utilisable avec le profileur Outils d’analyse des performances.

## <a name="syntax"></a>Syntaxe

```
/PROFILE
```

## <a name="remarks"></a>Notes

/Profile implique les options de l’éditeur de liens suivantes :

- [/OPT:REF](opt-optimizations.md)

- /OPT:NOICF

- [/INCREMENTAL:NO](incremental-link-incrementally.md)

- [/ FIXE : NO](fixed-fixed-base-address.md)

/ PROFIL entraîne l’éditeur de liens générer une section de réadressage dans l’image de programme.  Une section de réadressage permet au profileur transformer l’image de programme pour obtenir des données de profil.

**/ PROFIL** n’est disponible uniquement dans les versions entreprise (développement en équipe).  Pour plus d’informations sur PREfast, consultez [analyse du Code pour C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **avancé** page de propriétés.

1. Modifier le **profil** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>Pour définir cette option de l’éditeur de liens dans un projet Visual Studio CMake

**CMake** projet n’a pas un **Pages de propriétés**, les options de l’éditeur de liens peuvent être définies par modification du fichier CMakeLists.txt.

1. Ouvrez le fichier CMakeLists.txt dans le répertoire racine du projet.

1. Ajoutez le code ci-dessous. Pour plus d’informations, consultez [références de CMake](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. Régénérez votre solution.

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

