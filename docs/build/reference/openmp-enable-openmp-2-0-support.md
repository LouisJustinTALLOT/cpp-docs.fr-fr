---
title: -openmp (activer la prise en charge des OpenMP 2.0) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
dev_langs:
- C++
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe64011f48255a18aa8f8ccab7571533540a598a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378728"
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (Activer la prise en charge OpenMP 2.0)
Indique au compilateur de traiter `#pragma` [omp](../../preprocessor/omp.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/openmp  
```  
  
## <a name="remarks"></a>Notes  
 `#pragma omp` permet de spécifier [Directives](../../parallel/openmp/reference/openmp-directives.md) et [Clauses](../../parallel/openmp/reference/openmp-clauses.md). Si **/openmp** n’est pas spécifié dans une compilation, le compilateur ignore les clauses et directives OpenMP. [(Fonction OpenMP)](../../parallel/openmp/reference/openmp-functions.md) appels sont traités par le compilateur même si **/openmp** n’est pas spécifié.  
  
 Les applications compilées avec **/openmp** et **/CLR** peut uniquement être exécuté dans un processus de domaine d’application unique ; plusieurs domaines d’application ne sont pas pris en charge. Autrement dit, lorsque le constructeur de module (.cctor) est exécuté, il détecte le processus est compilé avec **/openmp** et si l’application est chargée dans un runtime par défaut. Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md), [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), et [l’initialisation d’assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).  
  
 Si vous essayez de charger une application compilée avec **/openmp** et **/CLR** dans un domaine d’application non-par défaut, un <xref:System.TypeInitializationException> exception est levée en dehors du débogueur et un Exception OpenMPWithMultipleAppdomainsException est levée dans le débogueur.  
  
 Ces exceptions peuvent également être déclenchées dans les situations suivantes :  
  
-   Si votre application compilée avec **/CLR**, mais pas avec **/openmp**, est chargée dans un domaine d’application de celui par défaut dont le processus inclut une application qui a été compilée avec **/ OpenMP**.  
  
-   Si vous passez vos **/CLR** application à un utilitaire, tel que regasm.exe ([Regasm.exe (outil Assembly Registration Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)), qui charge ses assemblys cibles dans un domaine d’application de celle par défaut.  
  
 Sécurité d’accès du code du common language runtime ne fonctionne pas dans les régions OpenMP. Si vous appliquez un attribut de sécurité de l’accès de code CLR en dehors d’une région parallèle, il ne sera en vigueur dans la région parallèle.  
  
 Microsoft recommande que vous n’écrivez pas **/openmp** applications permet partiellement approuvé appelants, à l’aide de <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, ou les attributs de sécurité accès du code CLR.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration** nœud.  
  
3.  Développez le **C/C++** nœud.  
  
4.  Sélectionnez le **langage** page de propriétés.  
  
5.  Modifier la **prise en charge OpenMP** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre certains effets du démarrage du pool de threads par rapport à threadpool après son démarrage. En supposant une x64, seul cœur, biprocesseur threadpool dure environ 16 ms au démarrage. Après cela existe cependant très faible coût pour le pool de threads.  
  
 Lorsque vous compilez avec **/openmp**, le deuxième appel à test2 ne s’exécute jamais plus longtemps que si vous compilez avec **/openmp-**, car il n’existe aucun démarrage du pool de threads. À un million d’itérations le **/openmp** version est plus rapide que la **/openmp-** version pour le deuxième appel à test2 et à 25 itérations **/openmp-** et **/openmp** versions register inférieure à celle de l’horloge.  
  
 Par conséquent, si vous n'avez qu’une seule boucle dans votre application et il s’exécute en moins de 15 ms (ajusté pour les charges mémoire approximatives sur votre ordinateur), **/openmp** peut ne pas convenir, mais si elle n’est pas plus que cela, vous pouvez envisager d’utiliser **/openmp**.  
  
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
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)