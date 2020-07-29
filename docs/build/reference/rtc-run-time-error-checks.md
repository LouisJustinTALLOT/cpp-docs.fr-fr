---
title: /RTC (Vérifications des erreurs au moment de l'exécution)
ms.date: 11/04/2016
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
ms.openlocfilehash: 49f0e4bace5f3dd199b58854e838204bd2cd5f3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222015"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Vérifications des erreurs au moment de l'exécution)

Utilisé pour activer et désactiver la fonctionnalité de vérification des erreurs au moment de l’exécution, conjointement avec le pragma [runtime_checks](../../preprocessor/runtime-checks.md) .

## <a name="syntax"></a>Syntaxe

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>Arguments

**1**<br/>
Équivalent de **/RTC** `su` .

**secteur**<br/>
Signale quand une valeur est assignée à un type de données plus petit et entraîne une perte de données. Par exemple, si une valeur de type `short 0x101` est assignée à une variable de type **`char`** .

Cette option signale les situations dans lesquelles vous envisagez de tronquer, par exemple, si vous souhaitez que les huit premiers bits d’un **`int`** retournés sous forme de **`char`** . Comme **/RTC** `c` provoque une erreur d’exécution si des informations sont perdues à la suite de l’assignation, vous pouvez masquer les informations dont vous avez besoin pour éviter une erreur d’exécution à la suite de **/RTC** `c` . Par exemple :

```
#include <crtdbg.h>

char get8bits(int value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

**x**<br/>
Active la vérification des erreurs au moment de l’exécution du frame de pile, comme suit :

- Initialisation des variables locales à une valeur différente de zéro. Cela permet d’identifier les bogues qui n’apparaissent pas lors de l’exécution en mode débogage. Il est plus probable que les variables de pile soient toujours égales à zéro dans une version Debug par rapport à une version Release en raison des optimisations du compilateur des variables de pile dans une version Release. Une fois qu’un programme a utilisé une zone de sa pile, il n’est jamais réinitialisé à 0 par le compilateur. Par conséquent, les variables de pile non initialisées suivantes qui utilisent la même zone de pile peuvent retourner des valeurs à partir de l’utilisation antérieure de cette mémoire de pile.

- Détection des dépassements et des sous-exécutions de variables locales telles que les tableaux. **/RTC** `s` ne détecte pas les dépassements lors de l’accès à la mémoire qui résulte du remplissage du compilateur au sein d’une structure. Le remplissage peut être effectué à l’aide de [align](../../cpp/align-cpp.md), [/Zp (alignement des membres de la structure)](zp-struct-member-alignment.md)ou [Pack](../../preprocessor/pack.md), ou si vous ordonnez des éléments de structure de telle sorte que le compilateur doit ajouter un remplissage.

- Vérification du pointeur de pile, qui détecte l’altération du pointeur de pile. La corruption du pointeur de pile peut être due à une incompatibilité de convention d’appel. Par exemple, à l’aide d’un pointeur de fonction, vous appelez une fonction dans une DLL exportée en tant que [__stdcall](../../cpp/stdcall.md) , mais vous déclarez le pointeur vers la fonction comme [__cdecl](../../cpp/cdecl.md).

**u**<br/>
Signale quand une variable est utilisée sans avoir été initialisée. Par exemple, une instruction qui génère `C4701` peut également générer une erreur au moment de l’exécution sous **/RTC** `u` . Toute instruction qui génère un [Avertissement du compilateur (niveau 1 et niveau 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) génère une erreur d’exécution sous **/RTC** `u` .

Toutefois, considérons le fragment de code suivant :

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Si une variable a pu être initialisée, elle ne sera pas signalée au moment de l’exécution par **/RTC** `u` . Par exemple, après qu’une variable a un alias à travers un pointeur, le compilateur n’effectue pas le suivi de la variable et signale des utilisations non initialisées. En effet, vous pouvez initialiser une variable en acceptant son adresse. L’opérateur & fonctionne comme un opérateur d’assignation dans ce cas.

## <a name="remarks"></a>Notes

Les vérifications des erreurs au moment de l’exécution vous permettent de trouver des problèmes dans votre code en cours d’exécution. Pour plus d’informations, consultez [Comment : utiliser les contrôles natifs à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks).

Si vous compilez votre programme sur la ligne de commande à l’aide de l’une des options du compilateur **/RTC** , les instructions pragma [optimize](../../preprocessor/optimize.md) de votre code échouent silencieusement. Cela est dû au fait que les vérifications des erreurs au moment de l’exécution ne sont pas valides dans une build (optimisée).

Vous devez utiliser **/RTC** pour les builds de développement ; **/RTC** ne doit pas être utilisé pour une version commerciale. Impossible d’utiliser **/RTC** avec les optimisations du compilateur ([options/o (optimiser le code)](o-options-optimize-code.md)). Une image de programme générée avec **/RTC** sera légèrement plus grande et légèrement plus lente qu’une image générée avec **/OD** (jusqu’à 5% plus lente qu’une build **/OD** ).

La directive de préprocesseur __MSVC_RUNTIME_CHECKS est définie lorsque vous utilisez une option **/RTC** ou [/gz](gz-enable-stack-frame-run-time-error-checking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **génération de code** .

1. Modifiez l’une des propriétés suivantes, ou les deux : vérifications de l' **exécution de base** ou **plus petite vérification du type**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Comment : utiliser les contrôles natifs au moment de l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks)
