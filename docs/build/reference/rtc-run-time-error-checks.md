---
title: -/RTC (vérifications des erreurs au moment de l’exécution) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a135c9c4e32ea7a54c45719eff503ff99509d3e7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378455"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Vérifications des erreurs au moment de l'exécution)
Utilisé pour activer et désactiver la fonctionnalité de vérification-erreur d’exécution, conjointement avec la [runtime_checks](../../preprocessor/runtime-checks.md) pragma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## <a name="arguments"></a>Arguments  
 `1`  
 Équivalent de **/RTC**`su`.  
  
 `c`  
 Signale quand une valeur est affectée à un type de données plus petit et entraîne une perte de données. Par exemple, si une valeur de type `short 0x101` est assigné à une variable de type `char`.  
  
 Cette option signale les situations dans lesquelles vous voulez tronquer, par exemple, si vous souhaitez que les huit premiers bits d’un `int` retourné comme un `char`. Étant donné que **/RTC.** `c` provoque une erreur d’exécution si les informations sont perdues suite à l’affectation, vous pouvez masquer les informations nécessaires pour éviter une erreur d’exécution à la suite de **/RTC** `c`. Par exemple :  
  
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
  
 `s`  
 Permet aux vérifications frame de pile erreur d’exécution, comme suit :  
  
-   Initialisation de variables locales à une valeur différente de zéro. Cela permet d’identifier les bogues n’apparaissent pas lors de l’exécution en mode débogage. Il est plus probable que les variables de pile sera toujours zéro dans une version debug par rapport à une version Release en raison des optimisations du compilateur des variables de pile dans une version Release. Une fois qu’un programme a utilisé une zone de sa pile, il n’est jamais réinitialisé à 0 par le compilateur. Par conséquent, les variables de pile suivantes non initialisées qui se produisent pour utiliser la même zone de pile peuvent retourner des valeurs créés à partir de l’utilisation de cette mémoire de la pile.  
  
-   Détection de dépassements et de sous-utilisation des variables locales, telles que des tableaux. **/RTC** `s` ne détecte pas les dépassements lors de l’accès mémoire qui résulte du remplissage du compilateur dans une structure. Remplissage peut se produire à l’aide de [aligner](../../cpp/align-cpp.md), [/Zp (alignement des membres de Struct)](../../build/reference/zp-struct-member-alignment.md), ou [pack](../../preprocessor/pack.md), ou si vous organisez les éléments de structure de manière à exiger au compilateur d’ajouter une marge intérieure.  
  
-   Vérification de pointeur de pile, qui détecte l’altération des pointeurs de pile. Altération des pointeurs de pile peut résulter d’une discordance de convention d’appel. Par exemple, à l’aide d’un pointeur de fonction, vous appelez une fonction dans une DLL qui est exportée en tant que [__stdcall](../../cpp/stdcall.md) , mais vous déclarez le pointeur à la fonction en tant que [__cdecl](../../cpp/cdecl.md).  
  
 `u`  
 Signale quand une variable est utilisée sans avoir été initialisée. Par exemple, une instruction qui génère `C4701` peut également générer une erreur au moment de l’exécution sous **/RTC**`u`. Toute instruction qui génère [Avertissement du compilateur (niveaux 1 et 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) génère une erreur au moment de l’exécution sous **/RTC**`u`.  
  
 Toutefois, considérez le fragment de code suivant :  
  
```cpp  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 Si une variable aurait pu être initialisée, elle n’est pas signalée au moment de l’exécution par **/RTC**`u`. Par exemple, une fois une variable alias via un pointeur, le compilateur pas suit la variable et de rapports utilise sans être initialisé. En effet, vous pouvez initialiser une variable par la prise de son adresse. Le & (opérateur) fonctionne comme un opérateur d’assignation dans ce cas.  
  
## <a name="remarks"></a>Notes  
 Vérifications des erreurs au moment de l’exécution sont un moyen de rechercher des problèmes dans votre code en cours d’exécution ; Pour plus d’informations, consultez [Comment : utiliser les contrôles d’exécution natifs](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
 Si vous compilez votre programme à la ligne de commande à l’aide de la **/RTC.** options du compilateur, les instructions du pragma [optimiser](../../preprocessor/optimize.md) figurant dans votre code échoue en silence. Il s’agit, car les vérifications des erreurs au moment de l’exécution ne sont pas valides dans une version Release (optimisée).  
  
 Vous devez utiliser **/RTC.** pour les builds de développement ; **/RTC.** ne doit pas être utilisé pour une version commerciale. **/RTC** ne peut pas être utilisé avec les optimisations du compilateur ([/O (optimiser le Code), Options](../../build/reference/o-options-optimize-code.md)). Une image de programme générée à l’aide **/RTC.** sera légèrement plus grande et plus lente qu’une image générée avec **/Od** (jusqu'à 5 pour cent plus lente qu’un **/Od** build).  
  
 La directive de préprocesseur __MSVC_RUNTIME_CHECKS sera définie lorsque vous utilisez un **/RTC.** option ou [GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **génération de Code** page de propriétés.  
  
4.  Modifier une ou les deux propriétés suivantes : **base Runtime vérifie** ou **vérification des types les plus petits**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Guide pratique pour utiliser les vérifications natives à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks)