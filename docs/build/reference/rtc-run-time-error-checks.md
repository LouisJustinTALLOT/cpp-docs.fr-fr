---
title: /RTC (Vérifications des erreurs au moment de l’exécution)
description: Options/RTC du compilateur Microsoft C/C++ pour les vérifications des erreurs au moment de l’exécution.
ms.date: 07/31/2020
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
ms.openlocfilehash: 888a81d0d5c21b0b85420a43d534c5b2742aa082
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765227"
---
# <a name="rtc-run-time-error-checks"></a>`/RTC` (Vérifications des erreurs au moment de l’exécution)

Utilisé pour activer et désactiver la fonctionnalité de vérification des erreurs au moment de l’exécution, conjointement avec le pragma [runtime_checks](../../preprocessor/runtime-checks.md) .

## <a name="syntax"></a>Syntaxe

> **`/RTC1`**\
> **`/RTCc`**\
> **`/RTCs`**\
> **`/RTCu`**

## <a name="arguments"></a>Arguments

**`/RTC1`**<br/>
Équivalent à **`/RTCsu`** .

**`/RTCc`**<br/>
Signale quand une valeur est assignée à un type de données plus petit et entraîne une perte de données. Par exemple, il signale si une **`short`** valeur de type de `0x0101` est assignée à une variable de type **`char`** .

Cette option peut signaler les situations dans lesquelles vous envisagez de tronquer. Par exemple, lorsque vous souhaitez que les 8 premiers bits d’un **`int`** retournés sous forme de **`char`** . En raison d' **`/RTCc`** une erreur d’exécution, si une affectation provoque une perte d’informations, commencez par masquer les informations dont vous avez besoin pour éviter l’erreur d’exécution. Par exemple :

```C
#include <crtdbg.h>

char get8bits(unsigned value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

Étant donné que **`/RTCc`** rejette le code qui est conforme à la norme, il n’est pas pris en charge par la bibliothèque C++ standard. Le code qui utilise **`/RTCc`** et la bibliothèque C++ standard peut provoquer l’erreur de compilateur [C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md). Vous pouvez définir `_ALLOW_RTCc_IN_STL` le silence de l’avertissement et utiliser l' **`/RTCc`** option.

**`/RTCs`**<br/>
Active la vérification des erreurs au moment de l’exécution du frame de pile, comme suit :

- Initialisation des variables locales à une valeur différente de zéro. Cette option permet d’identifier les bogues qui n’apparaissent pas lors de l’exécution en mode débogage. Il est plus probable que les variables de pile aient encore une valeur zéro dans une version Debug par rapport à une version Release. En raison des optimisations du compilateur des variables de pile dans une version Release. Une fois qu’un programme a utilisé une zone de sa pile, il n’est jamais réinitialisé à 0 par le compilateur. Cela signifie que toutes les variables de pile non initialisées qui utilisent la même zone de pile peuvent retourner ultérieurement des valeurs à partir de l’utilisation antérieure de cette mémoire de pile.

- Détection des dépassements et des sous-exécutions de variables locales telles que les tableaux. **`/RTCs`** ne détecte pas les dépassements lors de l’accès à la mémoire qui résulte du remplissage du compilateur au sein d’une structure. Le remplissage peut être effectué à l’aide de [`align`](../../cpp/align-cpp.md) , [ `/Zp` (alignement des membres de la structure)](zp-struct-member-alignment.md)ou [`pack`](../../preprocessor/pack.md) , ou si vous ordonnez des éléments de structure de telle sorte que le compilateur doit ajouter un remplissage.

- Vérification du pointeur de pile, qui détecte l’altération du pointeur de pile. La corruption du pointeur de pile peut être due à une incompatibilité de convention d’appel. Par exemple, à l’aide d’un pointeur de fonction, vous appelez une fonction dans une DLL exportée comme, [`__stdcall`](../../cpp/stdcall.md) mais vous déclarez le pointeur vers la fonction comme [`__cdecl`](../../cpp/cdecl.md) .

**`/RTCu`**<br/>
Signale quand une variable est utilisée sans avoir été initialisée. Par exemple, une instruction qui génère un avertissement C4701 peut également générer une erreur au moment de l’exécution sous **`/RTCu`** . Toute instruction qui génère un [Avertissement du compilateur (niveau 1 et niveau 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) génère une erreur au moment de l’exécution sous **`/RTCu`** .

Toutefois, considérons le fragment de code suivant :

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Si une variable a pu être initialisée, elle n’est pas signalée au moment de l’exécution par **`/RTCu`** . Par exemple, après qu’une variable a un alias à travers un pointeur, le compilateur n’effectue pas le suivi de la variable et signale des utilisations non initialisées. En effet, vous pouvez initialiser une variable en acceptant son adresse. L' **`&`** opérateur fonctionne comme un opérateur d’assignation dans cette situation.

## <a name="remarks"></a>Notes

Les vérifications des erreurs au moment de l’exécution vous permettent de trouver des problèmes dans votre code en cours d’exécution. Pour plus d’informations, consultez [Comment : utiliser les contrôles natifs à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks).

Vous pouvez spécifier plusieurs **`/RTC`** options sur la ligne de commande. Les arguments de l’option peuvent être combinés ; par exemple, **`/RTCcu`** est identique à **`/RTCc /RTCu`** .

Si vous compilez votre programme sur la ligne de commande à l’aide de l’une des **`/RTC`** Options du compilateur, les [`optimize`](../../preprocessor/optimize.md) instructions pragma de votre code échouent silencieusement. Cela est dû au fait que les vérifications des erreurs au moment de l’exécution ne sont pas valides dans une build (optimisée).

Utilisez **`/RTC`** pour les builds de développement ; N’utilisez pas **`/RTC`** pour une version Release. **`/RTC`** ne peut pas être utilisé avec les optimisations du compilateur ([ `/O` Options (optimiser le code)](o-options-optimize-code.md)). Une image de programme générée avec **`/RTC`** est légèrement plus grande et légèrement plus lente qu’une image générée avec **`/Od`** (jusqu’à 5% plus lent que la **`/Od`** génération).

La `__MSVC_RUNTIME_CHECKS` directive de préprocesseur est définie lorsque vous utilisez une **`/RTC`** option ou [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration**  >  **C/C++**  >  **génération de code** .

1. Modifiez l’une des propriétés suivantes, ou les deux : vérifications de l' **exécution de base** ou **plus petite vérification du type**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Guide pratique pour utiliser les vérifications natives à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks)
