---
title: /EH (Modèle de gestion des exceptions)
description: Guide de référence sur les options du compilateur Microsoft C++/EH (modèle de gestion des exceptions) dans Visual Studio.
ms.date: 08/25/2020
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
ms.openlocfilehash: 0d18d0f1d73b1de46b12262deecb2436c34e6176
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898386"
---
# <a name="eh-exception-handling-model"></a>`/EH` (Modèle de gestion des exceptions)

Spécifie la prise en charge du modèle de gestion des exceptions générée par le compilateur. Les arguments spécifient s’il faut appliquer la `catch(...)` syntaxe aux exceptions C++ structurées et standard, que le code ** extern « C »** est utilisé pour les throw exceptions et s’il faut optimiser certaines **`noexcept`** vérifications.

## <a name="syntax"></a>Syntaxe

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Arguments

**`a`**\
Active le déroulement de la pile C++ standard. Intercepte les exceptions structurées (asynchrones) et C++ standard (synchrones) lorsque vous utilisez la `catch(...)` syntaxe. **`/EHa`** remplace les **`/EHs`** **`/EHc`** arguments et.

**`s`**\
Active le déroulement de la pile C++ standard. Intercepte uniquement les exceptions C++ standard lorsque vous utilisez la `catch(...)` syntaxe. Sauf si **`/EHc`** est également spécifié, le compilateur suppose que les fonctions déclarées comme ** extern « C »** peuvent être throw une exception C++.

**`c`**\
Lorsqu’il est utilisé avec **`/EHs`** , le compilateur suppose que les fonctions déclarées comme ** extern « C »** ne sont jamais throw une exception C++. Elle n’a aucun effet lorsqu’elle est utilisée avec **`/EHa`** (autrement dit, **`/EHca`** est équivalent à **`/EHa`** ). **`/EHc`** est ignoré si **`/EHs`** ou **`/EHa`** n’est pas spécifié.

**`r`**\
Indique au compilateur de toujours générer des contrôles d’arrêt du runtime pour toutes les **`noexcept`** fonctions. Par défaut, les vérifications à **`noexcept`** l’exécution pour peuvent être optimisées si le compilateur détermine que la fonction appelle uniquement des fonctions non- throw ING. Cette option donne une conformité en C++ stricte au détriment d’un code supplémentaire. **`/EHr`** est ignoré si **`/EHs`** ou **`/EHa`** n’est pas spécifié.

**`-`**\
Efface l’argument de l’option précédente. Par exemple, **`/EHsc-`** est interprété comme **`/EHs /EHc-`** et est équivalent à **`/EHs`** .

**`/EH`** les arguments peuvent être spécifiés séparément ou combinés, dans n’importe quel ordre. Si plus d’une instance du même argument est spécifiée, la dernière remplace toutes les instances antérieures.  Par exemple, **`/EHr- /EHc /EHs`** est identique à **`/EHscr-`** et **`/EHscr- /EHr`** a le même effet que **`/EHscr`** .

## <a name="remarks"></a>Notes

### <a name="default-exception-handling-behavior"></a>Comportement de gestion des exceptions par défaut

Le compilateur génère toujours du code qui prend en charge la gestion asynchrone des exceptions structurées ( SEH ). Par défaut (autrement dit, si aucune **`/EHsc`** **`/EHs`** option, ou **`/EHa`** n’est spécifiée), le compilateur prend en charge les SEH gestionnaires dans la `catch(...)` clause C++ native. Toutefois, il génère également du code qui ne prend en charge que partiellement les exceptions C++. Le code de déroulement d’exception par défaut ne détruit pas les objets C++ automatiques en dehors des [`try`](../../cpp/try-throw-and-catch-statements-cpp.md) blocs qui sont hors de portée en raison d’une exception. Les fuites de ressources et le comportement non défini peuvent se produire quand une exception C++ est throw n.

### <a name="standard-c-exception-handling"></a>Gestion des exceptions C++ standard

La prise en charge complète du compilateur pour le modèle de gestion des exceptions C++ standard qui déroule en toute sécurité les objets de pile requiert **`/EHsc`** (recommandé), **`/EHs`** ou **`/EHa`** .

Si vous utilisez **`/EHs`** ou **`/EHsc`** , vos `catch(...)` clauses ne sont pas des catch exceptions structurées asynchrones. Les violations d’accès et les exceptions managées ne sont pas <xref:System.Exception?displayProperty=fullName> interceptées. De plus, les objets dans la portée lorsqu’une exception asynchrone se produit ne sont pas détruits, même si le code gère l’exception asynchrone. Ce comportement est un argument pour laisser les exceptions structurées non gérées. Au lieu de cela, considérez ces exceptions comme étant irrécupérables.

Lorsque vous utilisez **`/EHs`** ou **`/EHsc`** , le compilateur suppose que les exceptions ne peuvent se produire qu’au niveau d’une **`throw`** instruction ou d’un appel de fonction. Cette hypothèse permet au compilateur d’éliminer le code pour le suivi de la durée de vie de nombreux objets déroulés, ce qui peut réduire considérablement la taille du code. Si vous utilisez **`/EHa`** , votre image exécutable peut être plus grande et plus lente, car le compilateur n’optimise pas les **`try`** blocs de manière aussi agressive. Elle laisse également des filtres d’exception qui nettoient automatiquement les objets locaux, même si le compilateur ne voit pas de code pouvant faire l’objet d' throw une exception C++.

### <a name="structured-and-standard-c-exception-handling"></a>Gestion structurée et standard des exceptions C++

L' **`/EHa`** option de compilateur permet le déroulement sécurisé de la pile pour les exceptions asynchrones et les exceptions C++. Il prend en charge la gestion des exceptions structurées et C++ standard à l’aide de la clause C++ native `catch(...)` . Pour implémenter SEH sans spécifier **`/EHa`** , vous pouvez utiliser **`__try`** la **`__except`** syntaxe, et **`__finally`** . Pour plus d’informations, consultez [gestion structurée des exceptions](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Spécifier **`/EHa`** et try ING pour gérer toutes les exceptions à l’aide de `catch(...)` peuvent être dangereux. Dans la plupart des cas, les exceptions asynchrones sont irrécupérables et doivent être considérées comme telles. Si vous les interceptez sans les gérer, cela risque de provoquer une altération du processus et de générer des bogues difficiles à trouver et à résoudre.
>
> Bien que Windows et Visual C++ prennent en charge SEH , nous vous recommandons fortement d’utiliser la gestion des exceptions C++ standard ISO ( **`/EHsc`** ou **`/EHs`** ). Cela rend votre code plus portable et plus flexible. Il se peut que vous ayez parfois besoin d’utiliser SEH dans du code hérité ou pour des genres particuliers de programmes. Elle est requise dans le code compilé pour prendre en charge le common language runtime ( [`/clr`](clr-common-language-runtime-compilation.md) ), par exemple. Pour plus d’informations, consultez [gestion structurée des exceptions](../../cpp/structured-exception-handling-c-cpp.md).
>
> Nous vous recommandons de ne jamais lier les fichiers objets compilés à l’aide **`/EHa`** de à ceux compilés à l’aide de **`/EHs`** ou **`/EHsc`** dans le même module exécutable. Si vous devez gérer une exception asynchrone à l’aide **`/EHa`** de n’importe quel endroit de votre module, utilisez **`/EHa`** pour compiler l’ensemble du code du module. Vous pouvez utiliser la syntaxe de gestion structurée des exceptions dans le même module que le code compilé à l’aide de **`/EHs`** . Toutefois, vous ne pouvez pas mélanger la SEH syntaxe avec C++ **`try`** , **`throw`** et **`catch`** dans la même fonction.

Utilisez **`/EHa`** si vous souhaitez catch une exception levée par autre chose que **`throw`** . Cet exemple génère et catch es une exception structurée :

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

### <a name="exception-handling-under-clr"></a>Gestion des exceptions sous/CLR

L' **`/clr`** option implique **`/EHa`** (autrement dit, **`/clr /EHa`** est redondante). Le compilateur génère une erreur si **`/EHs`** ou **`/EHsc`** est utilisé après **`/clr`** . Les optimisations n’affectent pas ce comportement. Lorsqu’une exception est interceptée, le compilateur appelle les destructeurs de classe pour tous les objets qui se trouvent dans la même portée que l’exception. Si une exception n’est pas interceptée, ces destructeurs ne sont pas exécutés.

Pour plus d’informations sur les restrictions de gestion des exceptions sous **`/clr`** , consultez [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Vérifications des exceptions au moment de l’exécution

L' **`/EHr`** option force les contrôles d’arrêt de l’exécution dans toutes les fonctions qui ont un **`noexcept`** attribut. Par défaut, les vérifications à l’exécution peuvent être optimisées si le serveur principal du compilateur détermine qu’une fonction appelle uniquement *des fonctions non- throw ING* . throwLes fonctions non-ING sont des fonctions qui ont un attribut spécifiant qu’aucune exception ne peut être throw n. Elles incluent des fonctions marquées **`noexcept`** ,, `throw()` `__declspec(nothrow)` et, lorsque **`/EHc`** est spécifié, **`extern "C"`** functions. Les fonctions non-se throw comportent également du fait que le compilateur a déterminé qu’il n’y a pas throw d’inspection. Vous pouvez définir explicitement le comportement par défaut à l’aide de **`/EHr-`** .

Un attribut non- throw ING ne garantit pas que les exceptions ne peuvent pas être throw n par une fonction. Contrairement au comportement d’une **`noexcept`** fonction, le compilateur MSVC considère une exception throw n par une fonction déclarée à l’aide de `throw()` , `__declspec(nothrow)` ou **`extern "C"`** comme un comportement non défini. Les fonctions qui utilisent ces trois attributs de déclaration n’appliquent pas les vérifications d’arrêt de l’exécution pour les exceptions. Vous pouvez utiliser l' **`/EHr`** option pour vous aider à identifier ce comportement indéfini, en forçant le compilateur à générer des vérifications à l’exécution pour les exceptions non gérées qui échappent à une **`noexcept`** fonction.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Définir l’option dans Visual Studio ou par programme

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de configuration**  >  génération de code**C/C++**  >  **Code Generation**.

1. Modifiez la propriété **Activation des exceptions C++** .

   Sinon, affectez à **Activation des exceptions C++** la valeur **Non**, puis dans la page de propriétés **Ligne de commande** , dans la zone **Options supplémentaires** , ajoutez l'option de compilateur.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)\
[Erreurs et gestion des exceptions](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Spécifications d’exception ( throw )](../../cpp/exception-specifications-throw-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
