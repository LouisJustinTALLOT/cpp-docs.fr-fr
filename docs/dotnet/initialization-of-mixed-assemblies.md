---
title: Initialisation d'assemblys mixtes
description: Traitez les problèmes qui peuvent se produire pendant le chargement et l’initialisation d’assemblys mixtes.
ms.date: 09/26/2020
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 6767e6087999138f8e62d3c5a58f972b4e2149ed
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413812"
---
# <a name="initialization-of-mixed-assemblies"></a>Initialisation d'assemblys mixtes

Les développeurs Windows doivent toujours faire attention au verrouillage du chargeur lors de l’exécution du code pendant `DllMain` . Toutefois, il existe des problèmes supplémentaires à prendre en compte lors du traitement des assemblys en mode mixte C++/CLI.

Le code dans [DllMain](/windows/win32/Dlls/dllmain) ne doit pas accéder au CLR (Common Language Runtime) .net. Cela signifie que ne `DllMain` doit pas appeler de fonctions managées, directement ou indirectement ; aucun code managé ne doit être déclaré ou implémenté dans `DllMain` ; et aucun garbage collection ou chargement de bibliothèque automatique ne doit avoir lieu dans `DllMain` .

## <a name="causes-of-loader-lock"></a>Causes du verrouillage du chargeur

Avec l’introduction de la plateforme .NET, il existe deux mécanismes distincts pour charger un module d’exécution (EXE ou DLL) : un pour Windows, qui est utilisé pour les modules non managés et un pour le CLR, qui charge les assemblys .NET. Le problème du chargement de DLL mixtes se concentre autour du chargeur du système d’exploitation Microsoft Windows.

Lorsqu’un assembly contenant uniquement des constructions .NET est chargé dans un processus, le chargeur CLR peut effectuer toutes les tâches de chargement et d’initialisation nécessaires. Toutefois, pour charger des assemblys mixtes qui peuvent contenir du code natif et des données, le chargeur Windows doit également être utilisé.

Le chargeur Windows garantit qu’aucun code ne peut accéder au code ou aux données de cette DLL avant qu’elle ne soit initialisée. Elle garantit qu’aucun code ne peut charger la DLL de manière redondante pendant qu’elle est partiellement initialisée. Pour ce faire, le chargeur Windows utilise une section critique de processus global (souvent appelée « verrouillage du chargeur ») qui empêche l’accès non sécurisé pendant l’initialisation du module. Le processus de chargement est donc vulnérable pour de nombreux scénarios d’interblocage classiques. Pour les assemblys mixtes, les deux scénarios suivants augmentent le risque d’interblocage :

- Tout d’abord, si les utilisateurs tentent d’exécuter des fonctions compilées en langage MSIL (Microsoft Intermediate Language) quand le verrouillage du chargeur est maintenu (à partir de `DllMain` ou dans les initialiseurs statiques, par exemple), il peut provoquer un interblocage. Considérez le cas dans lequel la fonction MSIL fait référence à un type dans un assembly qui n’est pas encore chargé. Le CLR tente de charger automatiquement cet assembly, ce qui peut nécessiter le blocage du chargeur Windows sur le verrouillage du chargeur. Un blocage se produit, car le verrou du chargeur est déjà détenu par du code précédemment dans la séquence d’appel. Toutefois, l’exécution du langage MSIL pendant le verrouillage du chargeur ne garantit pas qu’un blocage se produira. C’est ce qui rend ce scénario difficile à diagnostiquer et à résoudre. Dans certains cas, par exemple quand la DLL du type référencé ne contient pas de constructions natives et que toutes ses dépendances ne contiennent pas de constructions natives, le chargeur Windows n’est pas obligé de charger l’assembly .NET du type référencé. En outre, l’assembly exigé ou ses dépendances natives/.NET mixtes ont peut-être déjà été chargés par un autre code. L’interblocage peut donc être difficile à prédire et peut varier selon la configuration de l’ordinateur cible.

- Deuxièmement, lors du chargement de dll dans les versions 1,0 et 1,1 du .NET Framework, le CLR supposait que le verrouillage du chargeur n’était pas maintenu et prenait plusieurs actions qui ne sont pas valides lors du verrouillage du chargeur. En supposant que le verrouillage du chargeur n’est pas maintenu est une hypothèse valide pour les dll purement .NET. Toutefois, étant donné que les dll mixtes exécutent des routines d’initialisation natives, elles nécessitent le chargeur Windows natif et, par conséquent, le verrou du chargeur. Ainsi, même si le développeur n’essayait pas d’exécuter des fonctions MSIL pendant l’initialisation de la DLL, il y avait toujours une petite possibilité d’interblocage non déterministe dans les versions 1,0 et 1,1 de .NET Framework.

Le non-déterminisme a été entièrement supprimé du processus de chargement de DLL mixtes Il a été accompli avec les modifications suivantes :

- Le CLR ne fait plus de fausses hypothèses lors du chargement de DLL mixtes.

- L’initialisation non managée et managée s’effectue en deux étapes distinctes et distinctes. L’initialisation non managée a lieu en premier (via `DllMain` ), et l’initialisation managée a lieu après, à l’aide d’un. Construction prise en charge par .NET `.cctor` . Ce dernier est totalement transparent pour l’utilisateur, sauf si **`/Zl`** ou **`/NODEFAULTLIB`** sont utilisés. Pour plus d’informations, consultez[ `/NODEFAULTLIB` (ignorer les bibliothèques)](../build/reference/nodefaultlib-ignore-libraries.md) et [ `/Zl` (omettre le nom de la bibliothèque par défaut)](../build/reference/zl-omit-default-library-name.md).

Le verrouillage du chargeur peut encore se produire, mais il est désormais détecté et se produit de façon déterministe. Si `DllMain` contient des instructions MSIL, le compilateur génère un avertissement [du compilateur d’avertissement (niveau 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). En outre, le CRT ou le CLR tente de détecter et de signaler les tentatives d’exécution du MSIL pendant le verrouillage du chargeur. La détection du CRT se traduit par le diagnostic du runtime C Run-Time Error R6033.

Le reste de cet article décrit les scénarios restants pour lesquels le langage MSIL peut s’exécuter sous le verrou du chargeur. Il montre comment résoudre le problème dans chacun de ces scénarios et les techniques de débogage.

## <a name="scenarios-and-workarounds"></a>Scénarios et solutions de contournement

Dans plusieurs cas de figure, le code utilisateur peut exécuter des instructions MSIL pendant le verrouillage du chargeur. Le développeur doit s’assurer que l’implémentation du code utilisateur ne tente pas d’exécuter des instructions MSIL dans chacune de ces circonstances. Les sous-sections suivantes décrivent toutes les possibilités tout en indiquant comment résoudre les problèmes dans les cas les plus courants.

### <a name="dllmain"></a>DllMain

La `DllMain` fonction est un point d’entrée défini par l’utilisateur pour une dll. Sauf indication contraire de l’utilisateur, la fonction `DllMain` est appelée chaque fois qu’un processus ou un thread s’attache à la DLL conteneur ou s’en détache. Dans la mesure où cet appel peut se produire alors que le verrouillage du chargeur est maintenu, aucune fonction `DllMain` fournie par l’utilisateur ne doit être compilée en langage MSIL. En outre, aucune fonction dans l’arborescence des appels associée à une racine `DllMain` ne peut être compilée en langage MSIL. Pour résoudre les problèmes ici, le bloc de code qui définit `DllMain` doit être modifié avec `#pragma unmanaged` . Il en va de même pour chaque fonction que `DllMain` appelle.

Dans les cas où ces fonctions doivent appeler une fonction qui nécessite une implémentation MSIL pour d’autres contextes d’appel, vous pouvez utiliser une stratégie de duplication dans laquelle une version .NET et une version native de la même fonction sont créées.

En guise d’alternative, si `DllMain` n’est pas nécessaire ou s’il n’a pas besoin d’être exécuté lors du verrouillage du chargeur, vous pouvez supprimer l’implémentation fournie par l’utilisateur `DllMain` , ce qui élimine le problème.

Si `DllMain` tente d’exécuter du code MSIL directement, l' [Avertissement du compilateur (niveau 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) se produit. Toutefois, le compilateur ne peut pas détecter les cas où `DllMain` appelle une fonction dans un autre module qui, à son tour, tente d’exécuter le langage MSIL.

Pour plus d’informations sur ce scénario, consultez [obstacles au diagnostic](#impediments-to-diagnosis).

### <a name="initializing-static-objects"></a>Initialisation d'objets statiques

L’initialisation d’objets statiques peut entraîner un interblocage si un initialiseur dynamique est exigé. Les cas simples (par exemple lorsque vous assignez une valeur connue au moment de la compilation à une variable statique) ne nécessitent pas d’initialisation dynamique, donc il n’y a aucun risque d’interblocage. Toutefois, certaines variables statiques sont initialisées par les appels de fonction, les appels de constructeur ou les expressions qui ne peuvent pas être évaluées au moment de la compilation. Ces variables requièrent tout du code pour s’exécuter pendant l’initialisation du module.

Le code suivant montre des exemples d’initialiseurs statiques qui exigent une initialisation dynamique : un appel de fonction, une construction d’objet et une initialisation de pointeur. (Ces exemples ne sont pas statiques, mais sont supposés avoir des définitions dans la portée globale, ce qui a le même effet.)

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

Ce risque d’interblocage varie selon que le module conteneur est compilé avec **`/clr`** et que MSIL sera exécuté. Plus précisément, si la variable statique est compilée sans **`/clr`** (ou dans un `#pragma unmanaged` bloc), et si l’initialiseur dynamique nécessaire pour l’initialiser entraîne l’exécution d’instructions MSIL, un interblocage peut se produire. Cela est dû au fait que, pour les modules compilés sans **`/clr`** , l’initialisation des variables statiques est effectuée par DllMain. En revanche, les variables statiques compilées avec **`/clr`** sont initialisées par le `.cctor` , une fois l’étape d’initialisation non managée terminée et le verrouillage du chargeur libéré.

Il existe un certain nombre de solutions à un interblocage provoqué par l’initialisation dynamique de variables statiques. Ils sont organisés ici à peu près dans le temps nécessaire pour résoudre le problème :

- Le fichier source contenant la variable statique peut être compilé avec **`/clr`** .

- Toutes les fonctions appelées par la variable statique peuvent être compilées en code natif à l’aide de la `#pragma unmanaged` directive.

- Clonez manuellement le code dont dépend la variable statique, en fournissant à la fois une version .NET et une version native avec des noms différents. Les développeurs peuvent ensuite appeler la version native à partir d’initialiseurs statiques natifs et appeler la version .NET ailleurs.

### <a name="user-supplied-functions-affecting-startup"></a>Fonctions fournies par l’utilisateur affectant le démarrage

Il existe plusieurs fonctions fournies par l’utilisateur dont dépendent les bibliothèques pour l’initialisation au démarrage. Par exemple, lors de la surcharge globale d’opérateurs en C++, tels que **`new`** les **`delete`** opérateurs et, les versions fournies par l’utilisateur sont utilisées partout, y compris dans l’initialisation et la destruction de la bibliothèque standard C++. Par conséquent, la bibliothèque standard C++ et les initialiseurs statiques fournis par l’utilisateur appellera toutes les versions fournies par l’utilisateur de ces opérateurs.

Si les versions fournies par l’utilisateur sont compilées en langage MSIL, ces initialiseurs tentent alors d’exécuter des instructions MSIL pendant que le verrouillage du chargeur est maintenu. Un fourni par `malloc` l’utilisateur a les mêmes conséquences. Pour résoudre ce problème, n’importe laquelle de ces surcharges ou définitions fournies par l’utilisateur doit être implémentée en tant que code natif à l’aide de la `#pragma unmanaged` directive.

Pour plus d’informations sur ce scénario, consultez [obstacles au diagnostic](#impediments-to-diagnosis).

### <a name="custom-locales"></a>Paramètres régionaux personnalisés

Si l’utilisateur fournit des paramètres régionaux globaux personnalisés, ces paramètres régionaux sont utilisés pour initialiser tous les futurs flux d’e/s, y compris les flux qui sont initialisés de manière statique. Si cet objet de paramètres régionaux globaux est compilé en langage MSIL, les fonctions membres d’objets de paramètres régionaux compilées en langage MSIL peuvent être appelées pendant que le verrouillage du chargeur est maintenu.

Il existe trois options pour résoudre ce problème :

Les fichiers sources contenant toutes les définitions de flux d’e/s globales peuvent être compilés à l’aide de l' **`/clr`** option. Elle empêche l’exécution de leurs initialiseurs statiques pendant le verrouillage du chargeur.

Les définitions de fonction de paramètres régionaux personnalisées peuvent être compilées en code natif à l’aide de la `#pragma unmanaged` directive.

Abstenez-vous de définir les paramètres régionaux personnalisés comme paramètres régionaux globaux tant que le verrouillage du chargeur n’a pas été désactivé. Configurez ensuite de façon explicite les flux d’E/S créés pendant l’initialisation avec les paramètres régionaux personnalisés.

## <a name="impediments-to-diagnosis"></a>Obstacles au diagnostic

Dans certains cas, il est difficile de détecter la source des blocages. Les sous-sections suivantes présentent ces scénarios et la façon de contourner ces problèmes.

### <a name="implementation-in-headers"></a>Implémentation dans les en-têtes

Dans des cas spécifiques, les implémentations de fonctions à l’intérieur des fichiers d’en-tête peuvent compliquer le diagnostic. Les fonctions inline et le code du modèle exigent que les fonctions soient spécifiées dans un fichier d’en-tête.  Le langage C++ spécifie la règle de définition unique, qui force toutes les implémentations de fonctions ayant le même nom à être sémantiquement équivalentes. L’éditeur de liens C++ n’a pas besoin de faire de considérations spéciales quand il fusionne des fichiers objets qui ont des implémentations en double d’une fonction donnée.

Dans les versions de Visual Studio antérieures à Visual Studio 2005, l’éditeur de liens choisit simplement la plus grande de ces définitions sémantiquement équivalentes. Elle est effectuée pour tenir compte des déclarations anticipées et des scénarios quand différentes options d’optimisation sont utilisées pour des fichiers sources différents. Il crée un problème pour les DLL natives et .NET mixtes.

Étant donné que le même en-tête peut être inclus à la fois par les fichiers C++ avec **`/clr`** activé et désactivé, ou un #include peut être encapsulé à l’intérieur d’un `#pragma unmanaged` bloc, il est possible d’avoir des versions MSIL et natives des fonctions qui fournissent des implémentations dans les en-têtes. Les implémentations MSIL et natives ont une sémantique différente pour l’initialisation dans le cadre du verrouillage du chargeur, ce qui viole en réalité la règle de définition unique. Par conséquent, lorsque l’éditeur de liens choisit l’implémentation la plus importante, il peut choisir la version MSIL d’une fonction, même si elle a été compilée explicitement en code natif ailleurs à l’aide de la `#pragma unmanaged` directive. Pour garantir qu’une version MSIL d’un modèle ou d’une fonction inline n’est jamais appelée pendant le verrouillage du chargeur, chaque définition de chaque fonction de ce type appelée sous verrouillage du chargeur doit être modifiée à l’aide de la `#pragma unmanaged` directive. Si le fichier d’en-tête provient d’un tiers, le moyen le plus simple d’effectuer cette modification consiste à envoyer et à dépiler la `#pragma unmanaged` directive autour de la directive #include pour le fichier d’en-tête incriminé. (Pour obtenir un exemple [, consultez managé, non managé](../preprocessor/managed-unmanaged.md) .) Toutefois, cette stratégie ne fonctionne pas pour les en-têtes qui contiennent un autre code qui doit appeler directement des API .NET.

À titre de commodité pour les utilisateurs confrontés au verrouillage du chargeur, l’éditeur de liens choisit l’implémentation native par rapport à l’implémentation managée en cas de présentation des deux implémentations. Cette valeur par défaut évite les problèmes ci-dessus. Toutefois, il existe deux exceptions à cette règle dans cette version en raison de deux problèmes non résolus avec le compilateur :

- L’appel à une fonction Inline s’effectue via un pointeur de fonction statique globale. Ce scénario n’est pasable, car les fonctions virtuelles sont appelées par le biais de pointeurs de fonction globale. Par exemple,

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>Diagnostic en mode débogage

Toutes les opérations de diagnostic des problèmes liés au verrouillage du chargeur doivent être effectuées sur des builds Debug. Les versions release ne peuvent pas produire de Diagnostics. Et, les optimisations effectuées en mode release peuvent masquer une partie du MSIL dans les scénarios de verrouillage du chargeur.

## <a name="how-to-debug-loader-lock-issues"></a>Comment déboguer les problèmes de verrouillage du chargeur

Le diagnostic que le CLR génère quand une fonction MSIL est appelée provoque l’interruption de l’exécution du CLR. Cela provoque à son tour l’interruption de Visual C++ débogueur en mode mixte lors de l’exécution du programme débogué in-process. Toutefois, lors de l’attachement au processus, it’sn’t possible d’obtenir une pile des appels managée pour le programme débogué à l’aide du débogueur mixte.

Pour identifier la fonction MSIL spécifique qui a été appelée pendant le verrouillage du chargeur, les développeurs doivent effectuer les étapes suivantes :

1. Vérifiez que les symboles de mscoree.dll et mscorwks.dll sont disponibles.

   Vous pouvez rendre les symboles disponibles de deux manières. Premièrement, les fichiers PDB de mscoree.dll et mscorwks.dll peuvent être ajoutés au chemin de recherche de symboles. Pour les ajouter, ouvrez la boîte de dialogue Options du chemin de recherche de symboles. (Dans le menu **Outils** , choisissez **options**. Dans le volet gauche de la boîte de dialogue **options** , ouvrez le nœud **débogage** , puis choisissez **symboles**.) Ajoutez le chemin d’accès aux fichiers mscoree.dll et mscorwks.dll PDB dans la liste de recherche. Ces PDB sont installés dans %VSINSTALLDIR%\SDK\v2.0\symbols. Choisissez **OK**.

   Deuxièmement, les fichiers PDB de mscoree.dll et mscorwks.dll peuvent être téléchargés à partir du serveur de symboles Microsoft. Pour configurer le serveur de symboles, ouvrez la boîte de dialogue des options du chemin de recherche de symboles. (Dans le menu **Outils** , choisissez **options**. Dans le volet gauche de la boîte de dialogue **options** , ouvrez le nœud **débogage** , puis choisissez **symboles**.) Ajoutez ce chemin de recherche à la liste de recherche : `https://msdl.microsoft.com/download/symbols` . Ajoutez un répertoire de cache de symboles à la zone de texte du cache du serveur de symboles. Choisissez **OK**.

1. Définissez le mode du débogueur en mode natif uniquement.

   Ouvrez la grille **Propriétés** du projet de démarrage dans la solution. Sélectionnez **Configuration Propriétés**  >  **débogage**. Affectez à la propriété **type de débogueur** la valeur **natif uniquement**.

1. Démarrez le débogueur (F5).

1. Lorsque le **`/clr`** diagnostic est généré, choisissez **Réessayer** , puis **arrêter**.

1. Ouvrez la fenêtre Pile des appels. (Dans la barre de menus, choisissez **Déboguer**  >  **Windows**  >  **Pile des appels**.) L' `DllMain` initialiseur incriminé ou statique est identifié par une flèche verte. Si la fonction incriminée n’est pas identifiée, les étapes suivantes doivent être effectuées pour la trouver.

1. Ouvrez la fenêtre **exécution** (dans la barre de menus, choisissez **Déboguer**les  >  **fenêtres**  >  **immédiates**.)

1. Entrez `.load sos.dll` dans la fenêtre **exécution** pour charger le service de débogage SOS.

1. Entrez `!dumpstack` dans la fenêtre **exécution** pour obtenir une liste complète de la **`/clr`** pile interne.

1. Recherchez la première instance (la plus proche du bas de la pile) de _CorDllMain (si est à `DllMain` l’origine du problème) ou _VTableBootstrapThunkInitHelperStub ou GetTargetForVTableEntry (si un initialiseur statique est à l’origine du problème). L’entrée de la pile juste en dessous de cet appel est l’appel de la fonction MSIL implémentée qui a tenté de s’exécuter pendant le verrouillage du chargeur.

1. Accédez au fichier source et au numéro de ligne identifiés à l’étape précédente, puis corrigez le problème à l’aide des scénarios et des solutions décrits dans la section scénarios.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre comment éviter le verrouillage du chargeur en déplaçant le code de `DllMain` dans le constructeur d’un objet global.

Dans cet exemple, il existe un objet managé global dont le constructeur contient l’objet managé qui se trouvait à l’origine `DllMain` . La deuxième partie de cet exemple référence l’assembly, en créant une instance de l’objet managé pour appeler le constructeur de module qui effectue l’initialisation.

### <a name="code"></a>Code

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker doesn't throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

Cet exemple illustre des problèmes d’initialisation d’assemblys mixtes :

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

Ce code génère la sortie suivante :

```Output
Module ctor initializing based on global instance of class.

Test called so linker doesn't throw away unused object.
```

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)
