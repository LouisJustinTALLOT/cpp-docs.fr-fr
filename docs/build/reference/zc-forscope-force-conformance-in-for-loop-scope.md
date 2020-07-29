---
title: /Zc:forScope (Forcer la conformité à la portée de la boucle for)
ms.date: 03/06/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
ms.openlocfilehash: b1173ad609a1b2c95d6cf118f4e2d5defeec5b9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234339"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (Forcer la conformité à la portée de la boucle for)

Permet d'implémenter un comportement C++ standard pour les boucles [for](../../cpp/for-statement-cpp.md) avec les extensions Microsoft ([/Ze](za-ze-disable-language-extensions.md)).

## <a name="syntax"></a>Syntaxe

> **/Zc : forScope**[ **-** ]

## <a name="remarks"></a>Notes

Le comportement standard consiste à laisser **`for`** l’initialiseur d’une boucle sortir de la portée après la **`for`** boucle. Sous **/Zc : forScope-** et [/Ze](za-ze-disable-language-extensions.md), l' **`for`** initialiseur de la boucle reste dans la portée jusqu’à ce que la portée locale se termine.

L’option **/Zc : forScope** est activée par défaut. **/Zc : forScope** n’est pas affecté quand l’option [/permissive-](permissive-standards-conformance.md) est spécifiée.

L’option **/Zc:forScope-** est déconseillée et sera supprimée dans une version ultérieure. L’utilisation de **/Zc:forScope-** génère l’avertissement D9035 de désapprobation.

Le code suivant est compilé sous **/Ze** , mais pas sous **/Za**:

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

Si vous utilisez **/Zc:forScope-**, l’avertissement C4288 (désactivé par défaut) est généré si une variable est dans la portée en raison de l’existence d’une déclaration dans une portée précédente. Pour illustrer ceci, supprimez les caractères `//` dans l’exemple de code pour déclarer `int i`.

Vous pouvez modifier le comportement au moment de l’exécution de **/Zc:forScope** en utilisant le pragma [conform](../../preprocessor/conform.md) .

Si vous utilisez **/Zc:forScope-** dans un projet contenant déjà un fichier .pch, un avertissement est généré, **/Zc:forScope-** est ignoré et la compilation continue en utilisant les fichiers .pch existants. Si vous souhaitez qu’un nouveau fichier. pch soit généré, utilisez [/Yc (créer un fichier d’en-tête précompilé)](yc-create-precompiled-header-file.md).

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés de la propriété de **configuration**  >  **C/C++**  >  **Language** .

1. Modifiez la propriété **Conformité forcée dans la portée d'une boucle For** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)<br/>
[/Za,/Ze (désactiver les extensions de langage)](za-ze-disable-language-extensions.md)<br/>
