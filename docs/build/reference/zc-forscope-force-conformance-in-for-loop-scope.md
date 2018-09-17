---
title: '/ Zc : forScope (forcer la conformité dans pour la portée d’une boucle) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef68f47fe8fdc430138a6961078139b48030b3d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723591"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (Forcer la conformité à la portée de la boucle for)

Permet d'implémenter un comportement C++ standard pour les boucles [for](../../cpp/for-statement-cpp.md) avec les extensions Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="syntax"></a>Syntaxe

> **/Zc:forScope**[**-**]

## <a name="remarks"></a>Notes

Le comportement standard consiste à laisser l’initialiseur d’une boucle **for** sortir de la portée après la boucle **for** . Sous **/Zc:forScope-** et [/Ze](../../build/reference/za-ze-disable-language-extensions.md), l’initialiseur de la boucle **for** reste dans la portée jusqu’à la fin de la portée locale.

Le **/Zc : forScope** option est activée par défaut. **/ Zc : forScope** n’est pas affecté lorsque le [/ permissive-](permissive-standards-conformance.md) option est spécifiée.

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

Si vous utilisez **/Zc:forScope-** dans un projet contenant déjà un fichier .pch, un avertissement est généré, **/Zc:forScope-** est ignoré et la compilation continue en utilisant les fichiers .pch existants. Si vous souhaitez générer un nouveau fichier .pch, utilisez [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md).

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **langage** page de propriétés.

1. Modifiez la propriété **Conformité forcée dans la portée d'une boucle For** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
[/Za, /Ze (Désactiver les extensions de langage)](../../build/reference/za-ze-disable-language-extensions.md)<br/>
