---
title: /PROFILE (Profileur des outils d'analyse des performances)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 26f4ba4efc20f5fee70b2937cdb943689c948888
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519913"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profileur des outils d'analyse des performances)

Génère un fichier de sortie utilisable avec le profileur Outils d’analyse des performances.

## <a name="syntax"></a>Syntaxe

```
/PROFILE
```

## <a name="remarks"></a>Notes

/Profile implique les options de l’éditeur de liens suivantes :

- [/ OPT : REF](../../build/reference/opt-optimizations.md)

- / OPT : NOICF

- [/ INCREMENTAL : NO](../../build/reference/incremental-link-incrementally.md)

- [/ FIXE : NO](../../build/reference/fixed-fixed-base-address.md)

/ PROFIL entraîne l’éditeur de liens générer une section de réadressage dans l’image de programme.  Une section de réadressage permet au profileur transformer l’image de programme pour obtenir des données de profil.

**/ PROFIL** n’est disponible uniquement dans les versions entreprise (développement en équipe).  Pour plus d’informations sur PREfast, consultez [analyse du Code pour C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **avancé** page de propriétés.

1. Modifier le **profil** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)