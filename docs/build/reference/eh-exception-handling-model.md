---
title: /EH (Modèle de gestion des exceptions)
description: Guide de référence des options de compilateur Microsoft CMD/EH (modèle de manutention d’exception) dans Visual Studio.
ms.date: 04/14/2020
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
no-loc:
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 68d6af657e7c20c0f5e84674dd91803beb35fba0
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396288"
---
# <a name="eh-exception-handling-model"></a>/EH (Modèle de gestion des exceptions)

Spécifie le support modèle de manutention d’exception généré par le compilateur. Les arguments précisent s’il faut appliquer `catch(...)` la syntaxe aux exceptions structurées et standard de C, si le throw **noexcept** ** extern ** code « C » est supposé à des exceptions, et s’il faut optimiser certaines vérifications.

## <a name="syntax"></a>Syntaxe

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Arguments

**`a`**\
Permet le dénouement standard de la pile CMD. Attrape à la fois des exceptions structurées (asynchrones) et `catch(...)` standard CMD (synchrones) lorsque vous utilisez la syntaxe. **`/EHa`** l’emporte **`/EHs`** à **`/EHc`** la fois et les arguments.

**`s`**\
Permet le dénouement standard de la pile CMD. Attrape uniquement des exceptions standard `catch(...)` de Cmd lorsque vous utilisez la syntaxe. À **`/EHc`** moins d’être également spécifié, le compilateur suppose throw que les fonctions déclarées ** extern « C »** peuvent être une exception C.

**`c`**\
Lorsqu’il **`/EHs`** est utilisé avec , le compilateur suppose throw que les fonctions déclarées comme ** extern "C"** jamais une exception C . Il n’a aucun **`/EHa`** effet lorsqu’il est utilisé avec (c’est-à-dire, **`/EHca`** est équivalent à **`/EHa`**). **`/EHc`** est ignoré **`/EHs`** **`/EHa`** si ou ne sont pas spécifiés.

**`r`**\
Indique au compilateur de toujours générer **noexcept** des contrôles de terminaison en temps d’exécution pour toutes les fonctions. Par défaut, les **noexcept** contrôles d’exécution peuvent être optimisés si le compilateur détermine que la fonction n’appelle que des fonctions non-jet. Cette option donne une conformité stricte À CMD au prix d’un code supplémentaire. **`/EHr`** est ignoré **`/EHs`** **`/EHa`** si ou ne sont pas spécifiés.

**`-`**\
Efface l’argument d’option précédent. Par exemple, **`/EHsc-`** est **`/EHs /EHc-`** interprété comme **`/EHs`**, et est équivalent à .

**`/EH`** les arguments peuvent être spécifiés séparément ou combinés, dans n’importe quel ordre. Si plus d’un cas du même argument est spécifié, le dernier l’emporte sur les précédents.  Par **`/EHr- /EHc /EHs`** exemple, est **`/EHscr-`** le **`/EHscr- /EHr`** même que , **`/EHscr`** et a le même effet que .

## <a name="remarks"></a>Notes

### <a name="default-exception-handling-behavior"></a>Comportement de manipulation par défaut d’exception

Le compilateur génère toujours du code qui prend enSEHcharge la manipulation d’exception structurée asynchrone ( ). Par défaut (c’est-à-dire, si **`/EHsc`** aucun, **`/EHs`**, ou **`/EHa`** option est spécifié), le compilateur prend en charge SEH les gestionnaires dans la clause native C . `catch(...)` Toutefois, il génère également du code qui ne prend en charge que partiellement les exceptions de C. Le code de dénouement par défaut n’détruit [try](../../cpp/try-throw-and-catch-statements-cpp.md) pas les objets automatiques CMD en dehors des blocs qui sortent de la portée en raison d’une exception. Les fuites de ressources et le comportement indéfini peuvent résulter lorsqu’une exception CMD est lancée.

### <a name="standard-c-exception-handling"></a>Manipulation d’exception standard de CMD

Support complet de compilateur pour le modèle standard de manutention **`/EHsc`** d’exception de CMD qui dénoue en toute sécurité les objets de pile exige (recommandé), **`/EHs`**, ou **`/EHa`**.

Si vous **`/EHs`** **`/EHsc`** utilisez ou, alors `catch(...)` vos catch clauses ne sont pas asynchrones exceptions structurées. Toute violation de <xref:System.Exception?displayProperty=fullName> l’accès et les exceptions gérées ne sont pas marquées. Et, les objets de portée lorsqu’une exception asynchrone se produit ne sont pas détruits, même si le code gère l’exception asynchrone. Ce comportement est un argument pour laisser les exceptions structurées sans manipulation. Au lieu de cela, considérez ces exceptions fatales.

Lorsque vous **`/EHs`** **`/EHsc`** utilisez ou, le compilateur suppose que **throw** les exceptions ne peuvent se produire à une déclaration ou à un appel de fonction. Cette hypothèse permet au compilateur d’éliminer le code pour le suivi de la durée de vie de nombreux objets non résiliables, ce qui peut réduire considérablement la taille du code. Si vous **`/EHa`** utilisez, votre image exécutable peut être plus grande **try** et plus lente, parce que le compilateur n’optimise pas les blocs aussi agressivement. Il laisse également dans les filtres d’exception qui nettoient automatiquement les objets throw locaux, même si le compilateur ne voit aucun code qui peut une exception C.

### <a name="structured-and-standard-c-exception-handling"></a>Manipulation d’exception structurée et standard de CMD

L’option **`/EHa`** compilateur permet un dénouement de la pile sécuritaire pour les exceptions asynchrones et les exceptions C. Il prend en charge le traitement des exceptions standard et `catch(...)` structurées en utilisant la clause native C. Pour SEH implémenter sans **`/EHa`** spécifier, vous pouvez utiliser le **__try**, **__except**, et **__finally** syntaxe. Pour plus d’informations, voir [Traitement d’exception structuré](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Spécifier **`/EHa`** et essayer de `catch(...)` gérer toutes les exceptions en utilisant peut être dangereux. Dans la plupart des cas, les exceptions asynchrones sont irrécupérables et doivent être considérées comme telles. Si vous les interceptez sans les gérer, cela risque de provoquer une altération du processus et de générer des bogues difficiles à trouver et à résoudre.
>
> Même si Windows et Visual SEHCMD support , nous vous recommandons fortement d’utiliser la manipulation d’exception ISO-standard CMD (ou**`/EHsc`** **`/EHs`**). Il rend votre code plus portable et flexible. Il peut encore y avoir SEH des moments que vous devez utiliser dans le code hérité ou pour certains types de programmes. Il est nécessaire dans le code compilé pour soutenir l’heure courante de course de langue ([/clr](clr-common-language-runtime-compilation.md)), par exemple. Pour plus d’informations, voir [Traitement d’exception structuré](../../cpp/structured-exception-handling-c-cpp.md).
>
> Nous vous recommandons de ne **`/EHa`** jamais lier **`/EHs`** les **`/EHsc`** fichiers d’objets compilés à l’aide de fichiers compilés à l’aide ou dans le même module exécutable. Si vous devez gérer une exception asynchrone en **`/EHa`** utilisant **`/EHa`** n’importe où dans votre module, utilisez-le pour compiler tout le code dans le module. Vous pouvez utiliser la syntaxe structurée de manipulation d’exception dans le même module que le code qui est compilé en utilisant **`/EHs`**. Cependant, vous ne pouvez SEH pas mélanger la **try** **throw** syntaxe avec C , , et **catch** dans la même fonction.

Utilisez **`/EHa`** si vous catch voulez une exception qui est **throw** soulevée par autre chose qu’un . Cet exemple génère et intercepte une exception structurée :

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to catch it using catch(...)
    try
    {
        int i = 0, j = 1;
        j /= i;   // This will throw a SE (divide by zero).
        printf("%d", j);
    }
    catch(...)
    {
        // catch block will only be executed under /EHa
        cout << "Caught an exception in catch(...)." << endl;
    }
}

int main()
{
    __try
    {
        fail();
    }

    // __except will only catch an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the catch(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>Manipulation d’exception sous /clr

L’option **`/clr`** **`/EHa`** implique (c’est-à-dire redondante). **`/clr /EHa`** Le compilateur génère une **`/EHs`** **`/EHsc`** erreur si **`/clr`** ou est utilisé après . Les optimisations n’affectent pas ce comportement. Lorsqu’une exception est capturée, le compilateur invoque les destructeurs de classe pour tous les objets qui sont dans la même portée que l’exception. Si une exception n’est pas prise, ces destructeurs ne sont pas exécutés.

Pour plus d’informations **`/clr`** sur les restrictions de traitement des exceptions en vertu , voir [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Vérifications d’exception en temps d’exécution

L’option **`/EHr`** oblige les contrôles de terminaison de temps d’exécution dans toutes les fonctions qui ont un **noexcept** attribut. Par défaut, les contrôles de temps d’exécution peuvent être optimisés si le back-end du compilateur détermine qu’une fonction n’appelle que des fonctions *non-lancement.* Les fonctions qui ne lèvent pas d’exceptions sont des fonctions qui ont un attribut spécifiant qu’aucune exception ne peut être levée. Ils comprennent des **noexcept** `throw()`fonctions marquées, , `__declspec(nothrow)`, et, quand **`/EHc`** est spécifié, ** extern "C"** fonctions. Les fonctions qui ne lèvent pas d’exceptions incluent également les fonctions que le compilateur a identifiées par inspection comme des fonctions ne levant pas d’exceptions. Vous pouvez définir explicitement le **`/EHr-`** comportement par défaut en utilisant .

Un attribut non-lancer n’est pas une garantie que les exceptions ne peuvent pas être jetées par une fonction. Contrairement au comportement **noexcept** d’une fonction, le compilateur MSVC `throw()`considère `__declspec(nothrow)`une exception jetée par une fonction déclarée en utilisant, , ou ** extern "C"** comme un comportement indéfini. Les fonctions qui utilisent ces trois attributs de déclaration n’appliquent pas les contrôles de terminaison en temps d’exécution pour les exceptions. Vous pouvez **`/EHr`** utiliser l’option pour vous aider à identifier ce comportement indéfini, en forçant le **noexcept** compilateur à générer des contrôles de temps d’exécution pour les exceptions non gérées qui échappent à une fonction.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Définissez l’option dans Visual Studio ou programmatiquement

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Configuration Properties** > **C/CMD** > Code**Generation**.

1. Modifiez la propriété **Activation des exceptions C++** .

   Sinon, affectez à **Activation des exceptions C++** la valeur **Non**, puis dans la page de propriétés **Ligne de commande** , dans la zone **Options supplémentaires** , ajoutez l'option de compilateur.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Voir aussi

[Options de compilateur MSVC](compiler-options.md)\
[Syntaxe MSVC Compiler Command-Line](compiler-command-line-syntax.md)\
[Erreurs et traitement des exceptions](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Spécificationsthrowd’exception ( )](../../cpp/exception-specifications-throw-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
