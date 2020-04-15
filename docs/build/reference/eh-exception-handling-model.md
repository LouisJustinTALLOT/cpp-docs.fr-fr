---
title: /EH (Modèle de gestion des exceptions)
ms.date: 08/14/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 8546b14995317afb57e4cc23a5d6f81c2172a1a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328292"
---
# <a name="eh-exception-handling-model"></a>/EH (Modèle de gestion des exceptions)

Spécifie le type de gestion des exceptions utilisé par le compilateur, quand optimiser la vérification des exceptions, et si les objets C++ hors de portée doivent être détruits en raison d’une exception. Si **/EH** n’est pas spécifié, le compilateur permet à votre code d’attraper à la fois des exceptions structurées asynchrones et des exceptions C , mais ne détruit pas les objets C ' qui sortent de portée en raison d’une exception asynchrone.

## <a name="syntax"></a>Syntaxe

> **/EH****'s**|**a**'[**c**][**r**] ]**-**

## <a name="arguments"></a>Arguments

**Un**<br/>
Le modèle de manipulation d’exception qui capture à la fois des exceptions asynchrones `catch(...)` (structurées) et synchrones (CMD) par l’utilisation de la syntaxe C.

**s**<br/>
Le modèle de manipulation d’exception qui attrape les exceptions synchrones (C) seulement et dit au compilateur de supposer que les fonctions déclarées comme **extern "C"** peuvent jeter une exception.

**C**<br/>
**S’il est** utilisé avec s (**/EHsc**), attrape seulement les exceptions de C et dit au compilateur de supposer que les fonctions déclarées comme **extern "C"** ne jettent jamais une exception C. **/EHca** équivaut à **/EHa**.

**R**<br/>
Indique au compilateur de toujours générer des contrôles de terminaison de temps d’exécution pour toutes les fonctions **noexcept.** Par défaut, les contrôles de **temps d’exécution pour noexcept** peuvent être optimisés si le compilateur détermine que la fonction appelle seulement des fonctions non-jet.

## <a name="remarks"></a>Notes

L'option de compilateur **/EHa** permet de prendre en charge la gestion des exceptions structurées asynchrones (SEH) avec la clause C++ native `catch(...)` . Pour implémenter SEH sans spécifier **/EHa**, vous pouvez utiliser le **__try**, **__except**, et **__finally** syntaxe. Bien que Windows et Visual C++ prennent en charge la gestion des exceptions structurées, nous vous recommandons fortement d'utiliser la gestion des exceptions C++ normalisée par l'ISO (**/EHs** ou **/EHsc**), car elle rend le code plus portable et plus flexible. Néanmoins, dans le code existant ou pour certains types de programmes, par exemple, dans le code compilé pour soutenir l’heure courante de l’exécution de la langue[(/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md))- vous pourriez encore avoir à utiliser SEH. Pour plus d'informations, consultez [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Il peut s’avérer dangereux de spécifier **/EHa** et de tenter de gérer toutes les exceptions à l’aide de `catch(...)` . Dans la plupart des cas, les exceptions asynchrones sont irrécupérables et doivent être considérées comme telles. Si vous les interceptez sans les gérer, cela risque de provoquer une altération du processus et de générer des bogues difficiles à trouver et à résoudre.

Si vous utilisez **/EHs** ou **/EHsc**, votre clause `catch(...)` n'intercepte pas les exceptions structurées asynchrones. Les violations d'accès et les exceptions <xref:System.Exception?displayProperty=fullName> non gérées ne sont pas interceptées. En outre, les objets contenus dans la portée lorsqu'une exception asynchrone est générée ne sont pas détruits même si l'exception asynchrone est gérée.

Si vous utilisez **/EHa**, l’image peut être plus grande et pourrait effectuer moins bien parce que le compilateur n’optimise pas un bloc **d’essai** aussi agressivement. Cela laisse également des filtres d’exception qui appellent automatiquement les destructeurs de tous les objets locaux, même si le compilateur ne voit pas de code pouvant lever une exception C++. Cette approche permet un déroulement sécurisé de la pile pour les exceptions asynchrones, ainsi que pour les exceptions C++. Lorsque vous utilisez **/EHs**, le compilateur suppose que les exceptions ne peuvent se produire à une déclaration **de lancer** ou à un appel de fonction. Cela permet au compilateur d'éliminer le code de suivi de la durée de vie de nombreux objets non déroulables, ce qui peut entraîner une réduction considérable de la taille du code.

Nous vous recommandons de ne pas lier les objets compilés en utilisant **/EHa** avec des objets compilés à l’aide **de /EHs** ou **/EHsc** dans le même module exécutable. Si vous devez gérer une exception asynchrone à l’aide de **/EHa** dans votre module, utilisez **/EHa** pour compiler l’ensemble du code du module. Vous pouvez utiliser la syntaxe structurée de manipulation d’exception dans le même module que le code qui est compilé en utilisant **/EHs**, mais vous ne pouvez pas mélanger la syntaxe SEH avec **essayer,** **jeter**, et **attraper** dans la même fonction.

Utilisez **/EHa** si vous voulez attraper une exception qui est soulevée par autre chose qu’un **lancer**. Cet exemple génère et intercepte une exception structurée :

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail() {   // generates SE and attempts to catch it using catch(...)
   try {
      int i = 0, j = 1;
      j /= i;   // This will throw a SE (divide by zero).
      printf("%d", j);
   }
   catch(...) {   // catch block will only be executed under /EHa
      cout<<"Caught an exception in catch(...)."<<endl;
   }
}

int main() {
   __try {
      fail();
   }

   // __except will only catch an exception here
   __except(EXCEPTION_EXECUTE_HANDLER) {
      // if the exception was not caught by the catch(...) inside fail()
      cout << "An exception was caught in __except." << endl;
   }
}
```

L'option **/EHc** exige la spécification de **/EHs** ou **/EHa** . **L’option /clr** implique **/EHa** (c’est-à-dire, **/clr** **/EHa** est redondant). Le compilateur génère une erreur si **/EHs** ou **/EHsc** est utilisé après **/clr**. Les optimisations n'affectent pas ce comportement. Lorsqu'une exception est interceptée, le compilateur appelle le ou les destructeurs de classe des objets compris dans la même portée que l'exception. Lorsqu'une exception n'est pas interceptée, ces destructeurs ne sont pas exécutés.

Pour plus d’informations sur les restrictions relatives à la gestion des exceptions sous **/clr**, consultez [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

L’option peut être effacée en utilisant le symbole **-**. Par exemple, **/EHsc-** est interprété comme **/EHs** **/EHc-** et est équivalent à **/EHs**.

**L’option compilateur /EHr** force les contrôles de terminaison de temps d’exécution dans toutes les fonctions qui ont un attribut **noexcept.** Par défaut, les vérifications à l’exécution peuvent être optimisées, si le compilateur back end détermine qu’une fonction appelle uniquement des fonctions *qui ne lèvent pas d’exceptions* . Les fonctions qui ne lèvent pas d’exceptions sont des fonctions qui ont un attribut spécifiant qu’aucune exception ne peut être levée. Cela comprend des fonctions marquées **noexcept** `throw()`, `__declspec(nothrow)`, et, lorsque **/EHc** est spécifié, **extern "C"** fonctions. Les fonctions qui ne lèvent pas d’exceptions incluent également les fonctions que le compilateur a identifiées par inspection comme des fonctions ne levant pas d’exceptions. Vous pouvez définir explicitement la valeur par défaut à l’aide de **/EHr-**.

Toutefois, l’attribut relatif à l’absence de levée d’exceptions ne garantit pas qu’une fonction ne peut pas lever d’exceptions. Contrairement au comportement d’une fonction **noexcept,** le compilateur MSVC `throw()` `__declspec(nothrow)`considère une exception jetée par une fonction déclarée en utilisant, , ou **extern "C"** comme un comportement indéfini. Les fonctions qui utilisent ces trois attributs de déclaration n’appliquent pas les vérifications d’arrêt au moment de l’exécution pour les exceptions. Vous pouvez utiliser l’option **/EHr** pour vous aider à identifier ce comportement indéfini, en forçant le compilateur à générer des contrôles de temps d’exécution pour les exceptions non gérées qui échappent à une fonction **noexcept.**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Configuration Properties** > **C/CMD** > Code**Generation**.

1. Modifiez la propriété **Activation des exceptions C++** .

   Sinon, affectez à **Activation des exceptions C++** la valeur **Non**, puis dans la page de propriétés **Ligne de commande** , dans la zone **Options supplémentaires** , ajoutez l'option de compilateur.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Gestion des erreurs et des exceptions](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
