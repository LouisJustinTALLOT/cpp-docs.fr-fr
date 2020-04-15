---
title: /openmp (Activez le support OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: d3454650bfaaacd756e5cfc73df056441a39f5ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336191"
---
# <a name="openmp-enable-openmp-support"></a>/openmp (Activez le support OpenMP)

Provoque le compilateur [`#pragma omp`](../../preprocessor/omp.md) de traiter les directives à l’appui de OpenMP.

## <a name="syntax"></a>Syntaxe

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__expérimental__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>Notes

`#pragma omp`est utilisé pour spécifier [les directives](../../parallel/openmp/reference/openmp-directives.md) et [les clauses](../../parallel/openmp/reference/openmp-clauses.md). Si **/openmp** n’est pas spécifié dans une compilation, le compilateur ignore les clauses et directives OpenMP. Les appels [fonctionnant OpenMP](../../parallel/openmp/reference/openmp-functions.md) sont traités par le compilateur même si **/openmp** n’est pas spécifié.

::: moniker range=">= vs-2019"

Le compilateur CMD prend actuellement en charge la norme OpenMP 2.0. Cependant, Visual Studio 2019 offre également maintenant des fonctionnalités SIMD. Pour utiliser SIMD, compilez en utilisant l’option **/openmp:experimental.** Cette option permet à la fois les fonctionnalités OpenMP habituelles, et les fonctionnalités SIMD OpenMP supplémentaires non disponibles lors de l’utilisation de l’interrupteur **/openmp.**

::: moniker-end

Les applications compilées à l’aide de **l’utilisation** à la fois /openmp et **/clr** ne peuvent être exécutées que dans un seul processus de domaine d’application. Les domaines d’application multiples ne sont pas pris en charge. Autrement dit, lorsque le`.cctor`constructeur de modules ( ) est exécuté, il détecte si le processus est compilé à l’aide **/openmp**, et si l’application est chargée dans un temps d’exécution non-default. Pour plus d’informations, voir [appdomain](../../cpp/appdomain.md), [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md)et [Initialization of Mixed Assemblies](../../dotnet/initialization-of-mixed-assemblies.md).

Si vous essayez de charger une application compilée à l’aide de **la fois /openmp** et **/clr** dans un domaine d’application non par défaut, une <xref:System.TypeInitializationException> exception est jetée à l’extérieur du débbugger, et une `OpenMPWithMultipleAppdomainsException` exception est jetée dans le débbugger.

Ces exceptions peuvent également être soulevées dans les situations suivantes :

- Si votre application est compilée à l’aide **de /clr** mais pas **/openmp**, et est chargée dans un domaine d’application non par défaut, où le processus comprend une application compilée à l’aide **de /openmp**.

- Si vous passez votre application **/clr** à un utilitaire, tel que [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), qui charge ses assemblages cibles dans un domaine d’application sans défaut.

La sécurité d’accès au code de l’heure courante ne fonctionne pas dans les régions OpenMP. Si vous appliquez un attribut de sécurité d’accès au code CLR en dehors d’une région parallèle, il ne sera pas en vigueur dans la région parallèle.

Microsoft ne vous recommande pas d’écrire **/openmp** applications qui permettent aux appelants partiellement fiables. N’utilisez <xref:System.Security.AllowPartiallyTrustedCallersAttribute>pas, ou n’importe quel code CLR accéder à des attributs de sécurité.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Élargir la page **Propriétés** > Configuration**C/CMD** > **Language.**

1. Modifier la propriété **OpenMP Support.**

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Exemple

L’échantillon suivant montre certains des effets de démarrage de pool de thread par rapport à l’utilisation du pool de threads après qu’il a commencé. En supposant un x64, seul noyau, double processeur, le pool de thread prend environ 16 ms pour démarrer. Après cela, il ya peu de frais supplémentaires pour le pool de fil.

Lorsque vous compilez à l’aide **/openmp**, le deuxième appel pour tester2 ne s’exécute jamais plus longtemps que si vous compilez à l’aide **/openmp-**, car il n’y a pas de démarrage de pool de thread. À un million d’itérations, la version **/openmp** est plus rapide que la version **/openmp-** pour le deuxième appel à tester2. À 25 itérations, les versions **openmp** **et/openmp** enregistrent moins que la granularité de l’horloge.

Si vous n’avez qu’une seule boucle dans votre application et qu’elle s’exécute en moins de 15 ms (ajustée pour les frais généraux approximatifs sur votre machine), **/openmp** peut ne pas être approprié. Si c’est plus élevé, vous pouvez envisager d’utiliser **/openmp**.

```cpp
// cpp_compiler_options_openmp.cpp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

volatile DWORD dwStart;
volatile int global = 0;

double test2(int num_steps) {
   int i;
   global++;
   double x, pi, sum = 0.0, step;

   step = 1.0 / (double) num_steps;

   #pragma omp parallel for reduction(+:sum) private(x)
   for (i = 1; i <= num_steps; i++) {
      x = (i - 0.5) * step;
      sum = sum + 4.0 / (1.0 + x*x);
   }

   pi = step * sum;
   return pi;
}

int main(int argc, char* argv[]) {
   double   d;
   int n = 1000000;

   if (argc > 1)
      n = atoi(argv[1]);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);
}
```

## <a name="see-also"></a>Voir aussi

[Options de compilateur MSVC](compiler-options.md) \
[Syntaxe MSVC Compiler Command-Line](compiler-command-line-syntax.md) \
[OpenMP dans MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
