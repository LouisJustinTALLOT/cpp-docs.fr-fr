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
ms.openlocfilehash: a830ff5b8ba4b7fcd95eb462f899f2eadce6de11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318548"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Vérifications des erreurs au moment de l'exécution)

Utilisé pour activer et désactiver la fonctionnalité de vérifications d’erreur d’exécution, conjointement avec le [runtime_checks](../../preprocessor/runtime-checks.md) pragma.

## <a name="syntax"></a>Syntaxe

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>Arguments

**1**<br/>
Équivalent de **/RTC**`su`.

**c**<br/>
Signale le moment où une valeur est affectée à un type de données plus petits et entraîne une perte de données. Par exemple, si une valeur de type `short 0x101` est affectée à une variable de type `char`.

Cette option signale les situations dans lesquelles vous souhaitez tronquer, par exemple, si vous souhaitez que les huit premiers bits d’un `int` retourné comme un `char`. Étant donné que **/RTC** `c` provoque une erreur si les informations sont perdues suite à l’affectation, vous pouvez masquer les informations nécessaires pour éviter une erreur d’exécution comme résultat de **/RTC** `c`. Exemple :

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

**s**<br/>
Permet aux vérifications frame de pile erreur d’exécution, comme suit :

- Initialisation de variables locales à une valeur différente de zéro. Cela permet d’identifier les bogues qui n’apparaissent pas lors de l’exécution en mode débogage. Il est très probable que les variables de pile sera toujours égal à zéro dans une version debug par rapport à une version Release en raison des optimisations du compilateur des variables de pile dans une version Release. Une fois qu’un programme a utilisé une zone de sa pile, il n’est jamais réinitialisé à 0 par le compilateur. Par conséquent, les variables de pile suivantes non initialisées qui se produisent pour utiliser la même zone de pile peuvent retourner des valeurs créés à partir de l’utilisation de cette mémoire de la pile.

- Détection des dépassements et de sous-utilisation des variables locales, tels que des tableaux. **/ RTC** `s` ne détecte pas les dépassements de lors de l’accès mémoire qui résulte de remplissage du compilateur dans une structure. Remplissage peut se produire à l’aide de [aligner](../../cpp/align-cpp.md), [/Zp (alignement des membres de Struct)](zp-struct-member-alignment.md), ou [pack](../../preprocessor/pack.md), ou si vous ordonnez les éléments de la structure de manière à exiger au compilateur d’ajouter une marge intérieure.

- Vérification de pointeur de pile, qui détecte l’altération de pointeur de pile. Corruption de pointeur de pile peut être dû à une discordance de convention d’appel. Par exemple, à l’aide d’un pointeur de fonction, vous appelez une fonction dans une DLL qui est exportée en tant que [__stdcall](../../cpp/stdcall.md) , mais vous déclarez le pointeur désignant la fonction en tant que [__cdecl](../../cpp/cdecl.md).

**u**<br/>
Signale le moment où une variable est utilisée sans avoir été initialisées. Par exemple, une instruction qui génère `C4701` peut également générer une erreur au moment de l’exécution sous **/RTC**`u`. Toute instruction qui génère [Avertissement du compilateur (niveaux 1 et 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) génère une erreur au moment de l’exécution sous **/RTC**`u`.

Toutefois, prenons le fragment de code suivant :

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Si une variable aurait pu être initialisée, elle n’est pas signalée au moment de l’exécution par **/RTC**`u`. Par exemple, une fois une variable alias via un pointeur, le compilateur pas suit la variable et signaler les utilisations non initialisées. En effet, vous pouvez initialiser une variable en tirant son adresse. Le & opérateur fonctionne comme un opérateur d’assignation dans cette situation.

## <a name="remarks"></a>Notes

Vérifications des erreurs au moment de l’exécution sont un moyen de rechercher des problèmes dans votre code en cours d’exécution. Pour plus d’informations, consultez [Comment : utiliser les vérifications natives à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks).

Si vous compilez votre programme en ligne de commande à l’aide de la **/RTC** options du compilateur, n’importe quel pragma [optimiser](../../preprocessor/optimize.md) instructions dans votre code échoue en silence. Il s’agit, car les vérifications des erreurs au moment de l’exécution ne sont pas valides dans une version Release (optimisée).

Vous devez utiliser **/RTC** pour les builds de développement ; **/RTC** ne doit pas être utilisé pour une version commerciale. **/ RTC** ne peut pas être utilisé avec les optimisations du compilateur ([/O Options (Optimize Code)](o-options-optimize-code.md)). Une image de programme générée avec **/RTC** sera légèrement plus grande et plus lente qu’une image générée avec **/Od** (jusqu'à 5 pour cent plus lent qu’un **/Od** build).

La directive du préprocesseur __MSVC_RUNTIME_CHECKS sera définie lorsque vous utilisez un **/RTC** option ou [/GZ](gz-enable-stack-frame-run-time-error-checking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **génération de Code** page de propriétés.

1. Modifiez une ou les deux des propriétés suivantes : **Des vérifications** ou **Type les plus petits cocher**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Guide pratique pour utiliser les vérifications natives à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks)
