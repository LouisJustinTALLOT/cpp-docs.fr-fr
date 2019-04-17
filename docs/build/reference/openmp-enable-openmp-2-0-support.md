---
title: /OpenMP (activer la prise en charge OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: caa06d89c590abd2b3a74a5a6b118d6ba4acd910
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674264"
---
# <a name="openmp-enable-openmp-support"></a>/OpenMP (activer la prise en charge OpenMP)

Indique au compilateur de traiter [ `#pragma omp` ](../../preprocessor/omp.md) directives pour prendre en charge OpenMP.

## <a name="syntax"></a>Syntaxe

::: moniker range=">= vs-2019"

> **/ openmp**\[**:**__expérimentale__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>Notes

`#pragma omp` permet de spécifier [Directives](../../parallel/openmp/reference/openmp-directives.md) et [Clauses](../../parallel/openmp/reference/openmp-clauses.md). Si **/OpenMP** n’est pas spécifié dans une compilation, le compilateur ignore les clauses et directives OpenMP. [Fonction OpenMP](../../parallel/openmp/reference/openmp-functions.md) appels sont traités par le compilateur même si **/OpenMP** n’est pas spécifié.

::: moniker range=">= vs-2019"

Le C++ compilateur prend actuellement en charge la norme OpenMP 2.0. Toutefois, Visual Studio 2019 offre désormais des fonctionnalités SIMD. Pour utiliser SIMD, compilez en utilisant le **/OpenMP : expérimentale** option. Cette option permet à la fois les fonctionnalités d’OpenMP habituelles, et des fonctionnalités supplémentaires OpenMP SIMD offertes non disponible lors de l’utilisation du **/OpenMP** basculer.

::: moniker-end

Les applications compilées à l’aide de deux **/OpenMP** et **/CLR** peut uniquement être exécuté dans un processus de domaine d’application unique. Plusieurs domaines d’application ne sont pas pris en charge. Autrement dit, lorsque le constructeur de module (`.cctor`) est exécuté, il détecte si le processus est compilé à l’aide de **/OpenMP**, et si l’application est chargée dans un runtime non définis par défaut. Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md), [/clr (Compilation pour le Common Language Runtime)](clr-common-language-runtime-compilation.md), et [l’initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).

Si vous essayez de charger une application compilée à l’aide de deux **/OpenMP** et **/CLR** dans un domaine d’application de ceux par défaut, un <xref:System.TypeInitializationException> exception est levée en dehors du débogueur et un `OpenMPWithMultipleAppdomainsException` exception est levée dans le débogueur.

Ces exceptions peuvent également être déclenchées dans les situations suivantes :

- Si votre application est compilée à l’aide de **/CLR** mais pas **/OpenMP**et est chargé dans un domaine d’application de ceux par défaut, où le processus inclut une application compilée à l’aide   **/OpenMP**.

- Si vous passez votre **/CLR** application à un utilitaire, tel que [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), qui charge ses assemblys cibles dans un domaine d’application de ceux par défaut.

Sécurité d’accès du code du common language runtime ne fonctionne pas dans les régions OpenMP. Si vous appliquez un attribut de sécurité de l’accès de code CLR en dehors d’une région parallèle, il ne sera en vigueur dans la région parallèle.

Microsoft ne vous recommandons d’écrire **/OpenMP** applications autorisant partiellement approuvé les appelants. N’utilisez pas <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, ou les attributs de sécurité accès du code CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez le **propriétés de Configuration** > **C /C++** > **langage** page de propriétés.

1. Modifier le **prise en charge OpenMP** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Exemple

L’exemple suivant montre certains effets du démarrage de pool de thread à la place le pool de threads après que qu’elle a démarré. Avec un x64 monocœur, biprocesseur, le pool de threads dure environ 16 ms démarrent. Après cela, il est peu coût supplémentaire pour le pool de threads.

Lorsque vous compilez à l’aide de **/OpenMP**, le deuxième appel à test2 ne s’exécute jamais plus longtemps que si vous compilez à l’aide de **/openmp-**, car il n’existe aucun démarrage de pool de thread. À un million d’itérations, la **/OpenMP** version est plus rapide que le **/openmp-** version pour le deuxième appel à test2. À 25 itérations, les deux **/openmp-** et **/OpenMP** versions register inférieure à celle de l’horloge.

Si vous n'avez qu’une seule boucle dans votre application et il s’exécute en moins de 15 ms (ajustés pour les charges mémoire approximatives sur votre ordinateur), **/OpenMP** peut ne pas convenir. S’il est plus élevé, vous souhaiterez à l’aide de **/OpenMP**.

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
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md) \
[OpenMP dans MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
