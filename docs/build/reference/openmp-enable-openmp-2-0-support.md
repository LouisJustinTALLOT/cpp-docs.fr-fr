---
description: En savoir plus sur:/OpenMP (activer la prise en charge d’OpenMP)
title: /OpenMP (activer la prise en charge d’OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: 818cd6167bf56b9948a3d9f455b0153b4302e8df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221980"
---
# <a name="openmp-enable-openmp-support"></a>/OpenMP (activer la prise en charge d’OpenMP)

Fait en sorte que le compilateur traite les directives pour la [`#pragma omp`](../../preprocessor/omp.md) prise en charge d’OpenMP.

## <a name="syntax"></a>Syntaxe

::: moniker range=">= msvc-160"

> **/OpenMP** \[ **:**__expérimental__]

::: moniker-end

::: moniker range="<= msvc-150"

> **/OpenMP**

::: moniker-end

## <a name="remarks"></a>Notes

`#pragma omp` est utilisé pour spécifier des [directives](../../parallel/openmp/reference/openmp-directives.md) et des [clauses](../../parallel/openmp/reference/openmp-clauses.md). Si **/OpenMP** n’est pas spécifié dans une compilation, le compilateur ignore les clauses et les directives OpenMP. Les appels de [fonction OpenMP](../../parallel/openmp/reference/openmp-functions.md) sont traités par le compilateur même si **/OpenMP** n’est pas spécifié.

::: moniker range=">= msvc-160"

Le compilateur C++ prend actuellement en charge la norme OpenMP 2,0. Toutefois, Visual Studio 2019 offre également des fonctionnalités SIMD. Pour utiliser SIMD, compilez à l’aide de l’option **/OpenMP : expérimental** . Cette option active à la fois les fonctionnalités OpenMP habituelles et les fonctionnalités OpenMP SIMD supplémentaires qui ne sont pas disponibles lors de l’utilisation du commutateur **/OpenMP** .

::: moniker-end

Les applications compilées à l’aide de **/OpenMP** et **/CLR** ne peuvent être exécutées que dans un seul processus de domaine d’application. Plusieurs domaines d’application ne sont pas pris en charge. Autrement dit, lorsque le constructeur de module ( `.cctor` ) est exécuté, il détecte si le processus est compilé à l’aide de **/OpenMP**, et si l’application est chargée dans un runtime autre que celui par défaut. Pour plus d’informations, consultez [AppDomain](../../cpp/appdomain.md), [/clr (compilation pour le Common Language Runtime)](clr-common-language-runtime-compilation.md)et [initialisation d’assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).

Si vous tentez de charger une application compilée à l’aide de **/OpenMP** et **/CLR** dans un domaine d’application autre que celui par défaut, une <xref:System.TypeInitializationException> exception est levée en dehors du débogueur, et une `OpenMPWithMultipleAppdomainsException` exception est levée dans le débogueur.

Ces exceptions peuvent également être générées dans les situations suivantes :

- Si votre application est compilée à l’aide de **/CLR** mais pas de **/OpenMP**, et est chargée dans un domaine d’application non défini par défaut, où le processus comprend une application compilée à l’aide de **/OpenMP**.

- Si vous transmettez votre application **/CLR** à un utilitaire, tel que [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), qui charge ses assemblys cibles dans un domaine d’application non défini par défaut.

La sécurité d’accès du code de common language runtime ne fonctionne pas dans les régions OpenMP. Si vous appliquez un attribut de sécurité d’accès du code CLR en dehors d’une région parallèle, il ne sera pas appliqué dans la région parallèle.

Microsoft ne recommande pas d’écrire des applications **/OpenMP** qui autorisent les appelants de confiance partielle. N’utilisez pas <xref:System.Security.AllowPartiallyTrustedCallersAttribute> , ou n’importe quel attribut de sécurité d’accès du code CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez la page **Propriétés de configuration**  >  **C/C++**  >  **Language** .

1. Modifiez la propriété **prise en charge OpenMP** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Exemple

L’exemple suivant montre certains des effets du démarrage du pool de threads par rapport à l’utilisation du pool de threads après son démarrage. En supposant qu’il s’agit d’un processeur x64, à noyau unique et à deux processeurs, le pool de threads prend environ 16 ms pour démarrer. Après cela, il y a peu de frais supplémentaires pour le pool de threads.

Quand vous compilez à l’aide de **/OpenMP**, le deuxième appel à test2 ne s’exécute jamais plus longtemps que si vous compilez à l’aide de **/OpenMP-**, car il n’y a pas de démarrage du pool de threads. À un million d’itérations, la version **/OpenMP** est plus rapide que la version **/OpenMP-** pour le deuxième appel à test2. À 25 itérations, les versions **/OpenMP-** et **/OpenMP** s’inscrivent moins que la granularité de l’horloge.

Si vous n’avez qu’une seule boucle dans votre application et qu’elle s’exécute en moins de 15 ms (ajustée pour la surcharge approximative sur votre ordinateur), **/OpenMP** peut ne pas être approprié. Si la valeur est supérieure, vous pouvez envisager d’utiliser **/OpenMP**.

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

[Options du compilateur MSVC](compiler-options.md) \
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md) \
[OpenMP dans MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
