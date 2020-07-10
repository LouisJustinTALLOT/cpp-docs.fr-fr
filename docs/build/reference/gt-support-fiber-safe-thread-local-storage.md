---
title: /GT (Prendre en charge le stockage local des threads avec fibres sécurisées)
description: L’option de compilateur MSVC/GT permet des optimisations sécurisées pour les données de stockage local des threads.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
ms.openlocfilehash: 1b1d9f6514cec8c3d247f86be063f2ac3e0dfe72
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180810"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>`/GT`(Prendre en charge le stockage local des threads à fibres sécurisées)

Prend en charge la sécurité des fibres pour les données allouées à l’aide du stockage local des threads statiques, c’est-à-dire des données allouées avec `__declspec(thread)` .

## <a name="syntax"></a>Syntaxe

> **`/GT`**

## <a name="remarks"></a>Notes

Les données déclarées avec `__declspec(thread)` sont référencées par l’intermédiaire d’un tableau de stockage local des threads (TLS). Le tableau TLS est un tableau d’adresses géré par le système pour chaque thread. Chaque adresse de ce tableau indique l’emplacement des données de stockage local des threads.

Une fibre est un objet léger qui se compose d’une pile et d’un contexte de Registre, et qui peut être planifié sur différents threads. Une fibre peut s’exécuter sur n’importe quel thread. Comme une fibre peut être permutée et redémarrée ultérieurement sur un autre thread, le compilateur ne doit pas en cache l’adresse du tableau TLS, ou l’optimise en tant que sous-expression commune sur un appel de fonction. **`/GT`** empêche ces optimisations.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation des **Propriétés de configuration**  >  **C/C++**  >  **Optimization** .

1. Modifiez la propriété **activer les optimisations à fibres sécurisées** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
