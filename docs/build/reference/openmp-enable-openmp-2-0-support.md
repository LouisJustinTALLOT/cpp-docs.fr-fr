---
title: /openmp (Activer la prise en charge OpenMP 2.0)
ms.date: 11/04/2016
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: f1edcc6d29a5b84106b3a5fd91d2446c34e0f7b9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807466"
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (Activer la prise en charge OpenMP 2.0)

Indique au compilateur de traiter `#pragma` [omp](../../preprocessor/omp.md).

## <a name="syntax"></a>Syntaxe

```
/openmp
```

## <a name="remarks"></a>Notes

`#pragma omp` permet de spécifier [Directives](../../parallel/openmp/reference/openmp-directives.md) et [Clauses](../../parallel/openmp/reference/openmp-clauses.md). Si **/OpenMP** n’est pas spécifié dans une compilation, le compilateur ignore les clauses et directives OpenMP. [Fonction OpenMP](../../parallel/openmp/reference/openmp-functions.md) appels sont traités par le compilateur même si **/OpenMP** n’est pas spécifié.

Les applications compilées avec **/OpenMP** et **/CLR** peut uniquement être exécuté dans un processus de domaine d’application unique ; plusieurs domaines d’application ne sont pas pris en charge. Autrement dit, lorsque le constructeur de module (.cctor) est exécuté, il détecte le processus est compilé avec **/OpenMP** et si l’application est chargée dans un runtime non définis par défaut. Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md), [/clr (Compilation pour le Common Language Runtime)](clr-common-language-runtime-compilation.md), et [l’initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).

Si vous essayez de charger une application compilée avec **/OpenMP** et **/CLR** dans un domaine d’application de ceux par défaut, un <xref:System.TypeInitializationException> exception sera levée en dehors du débogueur et un Exception OpenMPWithMultipleAppdomainsException être levée dans le débogueur.

Ces exceptions peuvent également être déclenchées dans les situations suivantes :

- Si votre application compilée avec **/CLR**, mais pas avec **/OpenMP**, est chargé dans un domaine d’application de ceux par défaut, mais où le processus comprend une application qui a été compilée avec **/ OpenMP**.

- Si vous passez votre **/CLR** application à un utilitaire, tel que regasm.exe ([Regasm.exe (outil Assembly Registration Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)), qui charge ses assemblys cibles dans un domaine d’application de ceux par défaut.

Sécurité d’accès du code du common language runtime ne fonctionne pas dans les régions OpenMP. Si vous appliquez un attribut de sécurité de l’accès de code CLR en dehors d’une région parallèle, il ne sera en vigueur dans la région parallèle.

Microsoft recommande que vous n’écrivez pas **/OpenMP** applications permet partiellement approuvé les appelants, à l’aide de <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, ou les attributs de sécurité accès du code CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **C/C++** nœud.

1. Sélectionnez le **langage** page de propriétés.

1. Modifier le **prise en charge OpenMP** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Exemple

L’exemple suivant montre certains effets du démarrage du pool de threads à la place le threadpool après son démarrage. En supposant une x64, monocœur, biprocesseur le threadpool dure environ 16 ms au démarrage. Après cela a cependant très faible coût pour le pool de threads.

Lorsque vous compilez avec **/OpenMP**, le deuxième appel à test2 ne s’exécute jamais plus longtemps que si vous compilez avec **/openmp-**, car il n’existe aucun démarrage du pool de threads. À un million d’itérations le **/OpenMP** version est plus rapide que le **/openmp-** version pour le deuxième appel à test2 et à 25 itérations **/openmp-** et **/OpenMP** versions register inférieure à celle de l’horloge.

Par conséquent, si vous n'avez qu’une seule boucle dans votre application et il s’exécute en moins de 15 ms (ajusté pour les charges mémoire approximatives sur votre ordinateur), **/OpenMP** peut ne pas convenir, mais si elle n’est rien de plus que cela, vous pouvez envisager d’utiliser **/OpenMP**.

```
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

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
